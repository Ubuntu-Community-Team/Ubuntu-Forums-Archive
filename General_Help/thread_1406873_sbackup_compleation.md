---
title: "sbackup compleation?"
date: 2010-02-14
forum: General Help
---

### Post by Jpenguin on 2010-02-14
I want a progress bar or something to tell me when sbackup is running. the number of files it has backed up/ % of completion


Also my backup drive is SATTA, always conected. How can I automount it on startup

---

### Post by Zill on 2010-02-14
Jpenguin:  AIUI, SBackup is designed to run as a background task with no feedback to the user once the backup process has commenced.  If you wish to see if the process is currently running, just use the following command in a terminal window:
```
top
```
(Hit "q" to quit the "top" command.)

If you wish to change SBackup functionality then I suggest you would need to modify the source code.

In order to automount the SATA drive, I suggest you edit your /etc/fstab file:

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

