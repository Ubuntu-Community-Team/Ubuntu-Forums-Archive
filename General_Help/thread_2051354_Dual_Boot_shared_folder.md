---
title: "Dual Boot shared folder"
date: 2012-09-01
forum: General Help
---

### Post by 0xicl33n on 2012-09-01
My situation is similiar to [this]("http://ubuntuforums.org/showthread.php?p=9172289")
Only i already have my partitions made, i want to have an NTFS partition that is mountable in linux and windows. Basically, i want to have it on ~/music so instead of copying music to *BOTH* operating systems, i have it accessible for both! The folder already exists, it has my music in it :P ive already used DD to reserve 10 gigs for a wordlist file on another location. What would the dd command be to make myself a 6 gig partition for music? And what should i put in /etc/fstab? Im assuming it will be detectable in windows 7 ? How can i make sure?



Ubuntu 10.04

---

### Post by oldfred on 2012-09-01
I do not understand. dd is for image copies. Not for creating partitions.

Use gparted to create a NTFS partition.

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by 0xicl33n on 2012-09-02
I forgot to meantion, i have the folder i made with dd as QUOTA. i followed a quota tutorial to create it. Gparted should work out, but [this]("http://souptonuts.sourceforge.net/quota_tutorial.html") is what i had done before
i probably should have mentioned that, i used the " **Creating a Virtual Filesystem**" part to make my image, i assumed NTFS could be done the same way. i suppose not, thanks for the help :D

---

