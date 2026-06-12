---
title: "Uninstalling ubuntu wubi"
date: 2012-05-26
forum: General Help
---

### Post by explorer414 on 2012-05-26
Hi everyone, i've uninstalled my wubi/ubuntu from the windows install/uninstall programs. It all went right, but i still have the folder "ubuntu" in my file system. Is it safe to delete the folder so i can have ubuntu removed completely from this computer?

Thx in advance!

---

### Post by Megaptera on 2012-05-26
If when you bootup it boots straight in to Windows with no Ubuntu option,then it should be OK to delete that folder.

---

### Post by bcbc on 2012-05-26
Why don't you post the log file (from the bottom it will have the log from the uninstaller)? That might show why it failed to remove it. Look in the %TEMP% directory and then the file should be wubi-xx.xx-revxxx.log (depending on what release).

It's possible it's a bug in the uninstaller, but also possible that there is some NTFS filesystem corruption (maybe if you had to force shutdown while running Ubuntu). If you find a problem deleting it manually, then run chkdsk /f on the drive.

---

