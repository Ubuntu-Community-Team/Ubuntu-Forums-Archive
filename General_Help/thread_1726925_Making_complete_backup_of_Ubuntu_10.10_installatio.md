---
title: "Making complete backup of Ubuntu 10.10 installation."
date: 2011-04-11
forum: General Help
---

### Post by Jetso on 2011-04-11
Okay, so I have a screwy hard drive and reports are showing that it's failing. Is there a program or something that will make .iso file of all my files on the Ubuntu partition, or is my best bet just compressing my /home/jetso folder and saving that file on a USB or something?

Any help would be appreciated.

---

### Post by lmarmisa on 2011-04-11
I recommend Clonezilla Live:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by Frogs Hair on 2011-04-11
There is also Remastersys , but I would backup the important files asap because the drive may fail before the complete backup is finished. [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by seawolf167 on 2011-04-11
> **lmarmisa said:**
> I recommend Clonezilla Live:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

+1 for Clonezilla - love it!

---

### Post by bodhi.zazen on 2011-04-11
Well, that is sort of the hard way of doing backups as the resulting image is huge and most likely unnecessary.

All you really need to back up is your home directory or any data you wish to keep.

From there you simply make a list of installed packages and use that list on a fresh install, then restore your data.

[http://savvyadmin.com/backup-and-restore-package-lists-in-ubuntu/](http://savvyadmin.com/backup-and-restore-package-lists-in-ubuntu/)

---

### Post by seawolf167 on 2011-04-11
Aye, that works as well - [rsync]("https://help.ubuntu.com/community/rsync") is perfect for [backing up]("https://help.ubuntu.com/community/BackupYourSystem") your directories. As for the packages, see bodhi's link.

---

### Post by sammiev on 2011-04-11
> **lmarmisa said:**
> I recommend Clonezilla Live:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

I use more than 1 operating system on my computer and Clonezilla does it all. So +1 for Clonezilla. GL :)

---

### Post by lmarmisa on 2011-04-11
I believe that complete backups are very useful. I recommend to have at least one. I like to make a complete backup of my computer every 3 or 4 months.

A backup of the home directory is very useful too. +1 for using rsync for this local backup.

---

### Post by Jetso on 2011-04-12
I will just try all 3. Mine as well be on the safe side. But I'll also copy some files onto another medium. 

Thanks for the quick, and detailed response(s)!

---

### Post by seawolf167 on 2011-04-12
> **Jetso said:**
> But I'll also copy some files onto another medium.

Make sure if you are using rsync or storing files directly that the other medium isn't a hard drive formatted NTFS, it should be ext3/4

---

### Post by Jetso on 2011-04-12
Okay, but why? I'm just curious.

---

### Post by seawolf167 on 2011-04-12
NTFS doesn't store ownership/permissions the same as ext so any files transfered to NTFS and back to ext wouldn't retain their ownership/permissions

---

