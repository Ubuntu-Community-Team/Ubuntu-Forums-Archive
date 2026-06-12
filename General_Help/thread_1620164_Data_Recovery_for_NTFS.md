---
title: "Data Recovery for NTFS"
date: 2010-11-12
forum: General Help
---

### Post by COKEDUDE on 2010-11-12
Could I please have some recommendations for Data Recovery for NTFS. These 2 websites look the most promising. 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.device-image.de/](http://www.device-image.de/)

---

### Post by Bitrate on 2010-11-12
Use Testdisk/PhotoRec for NTFS data recovery (It's free). Both these programs can be found on the SystemRescueCD ([www.sysresccd.org](www.sysresccd.org)). I have used them both with great success.

You can also install Testdisk via the cli with:

sudo apt-get install testdisk

---

### Post by COKEDUDE on 2010-11-16
> **Bitrate said:**
> Use Testdisk/PhotoRec for NTFS data recovery (It's free). Both these programs can be found on the SystemRescueCD ([www.sysresccd.org](www.sysresccd.org)). I have used them both with great success.

You can also install Testdisk via the cli with:

sudo apt-get install testdisk

Testdisk see's my first 10 folders. Unfortunately thx to a lovely ntfs limitation I can't see the rest of the folders :(. Would PhotoRec help me? I thought PhotoRec was for pictures.

---

### Post by Mark Phelps on 2010-11-16
Through painful personal experience, I have found the following to be true:
1) MS Windows utilities do the best job of recovering FAT/FAT32/NTFS partitions and files
2) Linux utilities do the best job of recovering Ext2/3/4 partitions and files.

IF you go to the Runtime Software site, you can download a trial version of RecoveryMyFiles.  You will need to install it on an MS Windows box, and you will have to then connect the problematic drive to that box -- but you will be able to see how good a job it does of detecting your files.

You can then decide whether it's worth the cost to get your files back -- because only the purchased version will do the actual recovery.

---

