---
title: "Ubuntu - Windows 7 File Intergration"
date: 2012-09-16
forum: General Help
---

### Post by daTomoT on 2012-09-16
Hi all. My netbook now has three partitions: C: Win 7, D: and a U: Ubuntu. Can I save to my D drive whether I boot Windows 7 or Ubuntu, and access the files from both of my boot drives? Essentially using D as a middle man for all of my files? How do I do this? I'd like to be able to access and edit my files regardless of which OS I boot onto.

~daT.

---

### Post by irv on 2012-09-16
> **daTomoT said:**
> Hi all. My netbook now has three partitions: C: Win 7, D: and a U: Ubuntu. Can I save to my D drive whether I boot Windows 7 or Ubuntu, and access the files from both of my boot drives? Essentially using D as a middle man for all of my files? How do I do this? I'd like to be able to access and edit my files regardless of which OS I boot onto.

~daT.

All you have to remember is Windows **_can't_** read ext3 or ext4 partitions but Ubuntu can read ext3, ext4, fat16, fat32, and NTFS partitions so if you make your D partition Fat32 or NTFS, both Windows and Linux can read it.

---

### Post by oldfred on 2012-09-16
Even with a separate shared data NTFS partition do not hibernate in Windows. If a file is open in the hibernation and you do something with Ubuntu you corrupt the Windows hibernation and lose the file.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD

** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

