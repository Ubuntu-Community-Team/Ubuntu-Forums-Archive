---
title: "Install Ubuntu FROM an external hard drive?"
date: 2011-05-16
forum: General Help
---

### Post by prettymess on 2011-05-16
Is there a way to install ubuntu from an external hard drive? A lot of what I've found while searching is mainly about how to install ubuntu ONTO an external hard drive, which isn't what I want.
 
Would it be the same as it is to install from a USB flash drive?
 
Also, I have a bunch of files I can't lose on my external hard drive, would it be possible to leave them on there and still install ubuntu on my laptop without formating my external hard drive?

---

### Post by prettymess on 2011-05-16
Is there a way to install ubuntu from an external hard drive? A lot of what I've found while searching is mainly about how to install ubuntu ONTO an external hard drive, which isn't what I want.
 
Would it be the same as it is to install from a USB flash drive?
 
Also, I have a bunch of files I can't lose on my external hard drive, would it be possible to leave them on there and still install ubuntu on my laptop without formating my external hard drive?

---

### Post by snowpine on 2011-05-16
[Unetbootin]("http://unetbootin.sourceforge.net/") might be able to help with this.

However, given your "I have a bunch of files I can't lose" statement, I would recommend purchasing a blank CD or a USB flash drive. Either of these options would be very inexpensive, and there would be no risk of losing your important files.

---

### Post by s.fox on 2011-05-17
Please do not create duplicate threads.  Thank you.

Threads merged.

---

### Post by oldfred on 2011-05-17
Most of the installers that create an install USB flash drive assume the drive is smaller and totally reformat the drive, so I would be very careful using any of them.

You can install grub2 and just copy the ISO to a partition. You then can loop mount that ISO. Most installs require the ISO to be extracted but loopmount allows use of the ISO without extraction. 

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

