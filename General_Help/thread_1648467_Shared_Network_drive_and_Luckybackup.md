---
title: "Shared Network drive and Luckybackup"
date: 2010-12-18
forum: General Help
---

### Post by cscj01 on 2010-12-18
I use LuckyBackup to backup my Data drive.  Prior to 10.10, I was able to backup my data by mounting a network drive at /mnt/cp2 and specifying that as my destination.  Under 10.10, the drive gets mounted automatically, and shows a location of smb://cp2/.  If I use that as a destination, LuckyBackup creates a directory named smb: and backs up my data to that directory in my filesystem.

How do I specify I want the destination to be the shared network drive to LuckyBackup?

---

### Post by cscj01 on 2010-12-20
The solution seems to be to mount the samba share locally.  With that, I'll close this issue.

---

