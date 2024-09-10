# Digital Forensics and Incident Response Unattended

![image](https://github.com/user-attachments/assets/da1475b4-61bd-4fd7-a766-54ef1658cbe3)

## Project Report: Investigation of Potential Data Exfiltration

### Task 1: Introduction

The investigation was initiated based on a report that a suspicious individual was seen exiting an office during lunch hours. The objective was to determine if any unauthorized activity occurred on the employee's computer between 12:05 PM and 12:45 PM on November 19, 2022. The analysis involved inspecting a disk image of the system, with a focus on identifying any files accessed and exfiltrated during this timeframe.

Tools provided for the investigation were located in the following directory:
C:\Users\THM-RFedora\Desktop\tools

### Task 2: Windows Forensics Review

A cheat sheet was provided to guide the forensic process, particularly for locating relevant file paths within the registry hives. This helped in identifying key locations to extract evidence, such as file access history and search queries made on the system.

### Task 3: Snooping Around

Objectives:

1. What file type was searched for using the search bar in Windows Explorer?
    
  Answer: .pdf

2. What top-secret keyword was searched for using the search bar in Windows Explorer?

   Answer: continental

Methodology:

The NTUSER.DAT file was analyzed using Registry Explorer to find the search history. The relevant path was located under:
NTUSER.DAT|Software|Microsoft|Windows|CurrentVersion\Explorer\Word Wheel Query.
By interpreting the data using the Unicode Strings category, both the file type .pdf and the keyword continental were identified.

![image](https://github.com/user-attachments/assets/2b139c3b-fd52-41f8-a0d1-68fa1cd1fdd3)

![image](https://github.com/user-attachments/assets/eab0486f-2aca-4cc4-af44-428c58821937)

### Task 4: Can’t Simply Open It

The investigation revealed that the threat actor found what they were looking for but encountered an obstacle that required additional resources to proceed. They downloaded a file to assist them in bypassing the obstacle.

Objectives:

1. What is the name of the downloaded file to the Downloads folder?


   Answer: 7z2201-x64.exe

2. When was the file downloaded? (YYYY-MM-DD HH:MM
    UTC)

   Answer: 2022-11-19 12:09:19 UTC

3. When was the PNG file opened? (YYYY-MM-DD HH:MM
    )
    Answer: 2022-11-19 12:10:21

Methodology:

Using Autopsy, the web downloads and recently opened files were reviewed. The downloaded file was identified as 7z2201-x64.exe, downloaded at the specified time. Further analysis revealed that a PNG file named "continental" was opened shortly after, using Registry Explorer to trace the specific file opening events.

![image](https://github.com/user-attachments/assets/0df3f4ff-f386-4409-b727-2bc531878924)

![image](https://github.com/user-attachments/assets/048170a8-dc37-4657-adbd-75e714c64bf0)

![image](https://github.com/user-attachments/assets/cedbd704-9092-45fa-9824-f320f5b79791)

### Task 5: Sending it Outside

The threat actor appeared to have successfully gathered the desired information and prepared it for exfiltration using an external method, as USB transfer was not possible.
Objectives:

1. How many times was the text file opened?

   Answer: 2

2. When was the text file last modified?

   Answer: 2022-11-19 12:12:35

3. What is the generated URL from the exfiltrated data?

   Answer: https://pastebin.com/1FQASAav

4. What is the string copied to the Pastebin URL?

   Answer: ne7AIRhi3pdesy9RnOrN

Methodology:

The JLECmd tool was used to parse the directory and sift through the results based on the given timeframe. This revealed the number of times the text file was opened and its modification time. By cross-referencing the web history in Autopsy, the Pastebin URL was identified along with the exfiltrated string.

![image](https://github.com/user-attachments/assets/865b6a9b-b97b-4df7-9a9b-2d156792a163)

![image](https://github.com/user-attachments/assets/db680410-f636-44ca-9a8e-98904b1d4eb6)

![image](https://github.com/user-attachments/assets/ae940211-7f3d-431f-8cb4-c02c456682b9)

### Task 6: Conclusion

The investigation determined that an unknown individual accessed the employee’s computer during the specified lunch break, conducted a targeted search for sensitive information, and successfully exfiltrated data via a Pastebin URL. While the identity of the perpetrator remains unknown, it is evident that they were highly familiar with what they were searching for and how to obtain it.

This concludes the forensic investigation. The findings confirm unauthorized access and data exfiltration. Further security measures should be implemented to prevent such incidents in the future.


