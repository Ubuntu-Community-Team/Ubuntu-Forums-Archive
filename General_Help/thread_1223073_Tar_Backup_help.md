---
title: "Tar Backup help"
date: 2009-07-25
forum: General Help
---

### Post by Manyette on 2009-07-25
Question re: Backup using tar.  It has been my habit to backup to an external hard disk attached to the machine via USB. Upon attempting to backup the entire system, I of course found that since the USB drive was a part of the system, it was trying to back up itself as well as the system hard drive.  Searched the man page, and various online tutorials, and haven't found a solution to excluding the drive I'm backing up to using tar.  I realize that I could create a file list and use the -t command, but it seems there should be an easier way.  Am I missing something, or should I just start building a file list?  Thanks for any help.  - - - Don

---

### Post by wojox on 2009-07-25
Here you go:

[http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

---

### Post by Manyette on 2009-07-25
> **wojox said:**
> Here you go:

[http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

Well, that doesn't use tar, does it.  Matter of fact I tried sbackup, and was not happy with it.  Did two backups using it, and found both unusable when I needed them.  Perhaps my fault, I don't know, bit I don't trust it at this point.  But thanks anyway - - - Don

---

### Post by louieb on 2009-07-25
Heres the classic tar howto [**Howto: Backup and restore your system**]("http://ubuntuforums.org/showthread.php?t=35087&highlight=tar+backup")

about the same as above with some stuff addd [http://ubuntuforums.org/showthread.php?t=81311&highlight=backup](http://ubuntuforums.org/showthread.php?t=81311&highlight=backup)

I prefer Partimage.  [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522")

---

### Post by mike2357 on 2009-07-25
The tar command allows you to exclude files from the backup.  For instance, if your usb device is mounted on /mnt/usb_device, your tar command to back up everything to the device (except what's on the device) would be something like this:

cd /
tar cvf /mnt/usb_device/backup_file.tar --exclude=/mnt/usb_device .

Run "man tar" for more details.

---

### Post by Manyette on 2009-07-26
LouieB and Mike 2357 thanks to you both.  That was exactly what I needed and it works just fine.  Appreciate the advice.  Thanks again - - - Don

---

