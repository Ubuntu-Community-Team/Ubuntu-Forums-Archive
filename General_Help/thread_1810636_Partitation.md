---
title: "Partitation"
date: 2011-07-23
forum: General Help
---

### Post by Brandon HQI on 2011-07-23
Hey Ive been using ubuntu almost a year now but i usually intall it using wubi but now i would like to partiation my harddisk drive an install it but i dont now how? cold sum one please tell mi how and would 10GB be enough space to install it if I jus want to customize an play around with it. (Usually I would give more momory but i wanna try an install MAC OS on a partiation also) :popcorn:

---

### Post by 2F4U on 2011-07-23
You should plan at least for a root partition (/) and a swap partition. 10 GB for / is not very much, but may be OK if you don't intend to store data in it. If you intend to store date, it may be worth to think about a separate /home partition.

---

### Post by oldfred on 2011-07-23
The new version wants 4.4GB as a minimum, so 10GB will work. I normally install to 20-25GB but keep all data elsewhere.

How many partitions has your system used. Many come with all 4 primary partitions used. You then have to decide which to delete and then create an extended partition to hold as many logical partitions as you want.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Backup and make recovery DVDs and a windows repair CD.
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Blasphemist on 2011-07-23
Please see this for migration of wubi to full install, with pictures. [http://ubuntu-with-wubi.blogspot.com/2011/05/how-to-migrate-in-pictures.html](http://ubuntu-with-wubi.blogspot.com/2011/05/how-to-migrate-in-pictures.html)

10 GB is plenty if you don't need to save music, pictures, iso's, etc. If you download and use this boot info script (instructions in the link) and paste the results in code tags we could better recommend partitioning. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

