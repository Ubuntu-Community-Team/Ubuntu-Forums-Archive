---
title: "Natty upgrade USB problem, PLEASE HELP!!"
date: 2011-05-12
forum: General Help
---

### Post by salterlee on 2011-05-12
Hi all. I've got the same problem. All my USB external drives (hard drive and USB memory stick) only mount when forced with 
lee@lee-desktop:~$ sudo mount /dev/sde1 /media/usbflsh
I can't eject them via nautilus, I have to umount. 

PLEASE can someone with a bit of experience HELP?!!!! 

I've ran this:
lee@lee-desktop:~$ sudo blkid
/dev/sda1: LABEL="2nd1" UUID="50F45961F45949FC" TYPE="ntfs" 
/dev/sda3: LABEL="2nd2" UUID="01C6A9EAB5687100" TYPE="ntfs" 
/dev/sda5: UUID="be06f940-f320-4a71-a75a-66a367249d92" TYPE="ext4" 
/dev/sda6: UUID="5f96f190-c1c7-44db-b9c0-95f769e3b927" TYPE="swap" 
/dev/sdb1: LABEL="Windows" UUID="E434FC7334FC4A56" TYPE="ntfs" 
/dev/sdc1: LABEL="New Volume" UUID="5276E69976E67D5B" TYPE="ntfs" 
/dev/sdd1: UUID="ACA4E9EFA4E9BC48" TYPE="ntfs" 
/dev/sde1: UUID="901E-2C40" TYPE="vfat" 

The last two entries are my external HDD and USB flash drive respectively.

FStab (Which I DO NOT understand) looks like this
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=be06f940-f320-4a71-a75a-66a367249d92    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=50F45961F45949FC    /media/2nd1    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.utf8    0    0
#Entry for /dev/sda3 :
UUID=01C6A9EAB5687100    /media/2nd2    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.utf8    0    0
#Entry for /dev/sdc1 :
UUID=5276E69976E67D5B    /media/New_Volume    ntfs-3g    defaults,locale=en_GB.utf8    0    0
#Entry for /dev/sdb1 :
UUID=E434FC7334FC4A56    /media/Windows    ntfs-3g    defaults,locale=en_GB.utf8    0    0
#Entry for /dev/sdd1 :
UUID=ACA4E9EFA4E9BC48    /media/sdd1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda6 :
UUID=5f96f190-c1c7-44db-b9c0-95f769e3b927    none    swap    sw    0    0



PLLLLLLLLLEEEEEEEEEASEEE HEEEEELP!!!

---

### Post by salterlee on 2011-05-12
Hi all. I upgraded to Natty (when everything was working fine) but since then Ubuntu refuses to automatically mount USB storage devices, and the manual mount doesn't let me write to disk. The USB flash drive I have works on my Ubuntu (Natty) netbook and on my XP installation on my desktop (so there's nothing wrong with the device or computer), but nothing happens when I plug it in on my desktop - the mouse works fine!

I can force with
lee@lee-desktop:~$ sudo mount /dev/sde1 /media/usbflsh
I can't eject them via nautilus, I have to umount, which only works sometimes, but I cannot write.

PLLLLLLEEEEEEEEEEEASSE help as I really need to work!!!!

PLEASE can someone with a bit of experience HELP?!!!! 

I've ran this:
lee@lee-desktop:~$ sudo blkid
/dev/sda1: LABEL="2nd1" UUID="50F45961F45949FC" TYPE="ntfs" 
/dev/sda3: LABEL="2nd2" UUID="01C6A9EAB5687100" TYPE="ntfs" 
/dev/sda5: UUID="be06f940-f320-4a71-a75a-66a367249d92" TYPE="ext4" 
/dev/sda6: UUID="5f96f190-c1c7-44db-b9c0-95f769e3b927" TYPE="swap" 
/dev/sdb1: LABEL="Windows" UUID="E434FC7334FC4A56" TYPE="ntfs" 
/dev/sdc1: LABEL="New Volume" UUID="5276E69976E67D5B" TYPE="ntfs" 
/dev/sdd1: UUID="ACA4E9EFA4E9BC48" TYPE="ntfs" 
/dev/sde1: UUID="901E-2C40" TYPE="vfat" 

The last two entries are my external HDD and USB flash drive respectively.

FStab (Which I DO NOT understand) looks like this
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=be06f940-f320-4a71-a75a-66a367249d92    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=50F45961F45949FC    /media/2nd1    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.utf8    0    0
#Entry for /dev/sda3 :
UUID=01C6A9EAB5687100    /media/2nd2    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.utf8    0    0
#Entry for /dev/sdc1 :
UUID=5276E69976E67D5B    /media/New_Volume    ntfs-3g    defaults,locale=en_GB.utf8    0    0
#Entry for /dev/sdb1 :
UUID=E434FC7334FC4A56    /media/Windows    ntfs-3g    defaults,locale=en_GB.utf8    0    0
#Entry for /dev/sdd1 :
UUID=ACA4E9EFA4E9BC48    /media/sdd1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda6 :
UUID=5f96f190-c1c7-44db-b9c0-95f769e3b927    none    swap    sw    0    0

---

### Post by salterlee on 2011-05-12
..and for some reason Disk Utility won't load - I have tried uninstalling and reinstalling, but no luck.

---

### Post by salterlee on 2011-05-12
Just realised that my DVD drives are not recognised either...please heeeeeelp!!!

---

### Post by salterlee on 2011-05-16
Hi all. I upgraded to Natty (when everything was working fine) but since  then Ubuntu refuses to automatically mount USB storage devices, and the  manual mount doesn't let me write to disk. The USB flash drive I have  works on my Ubuntu (Natty) netbook and on my XP installation on my  desktop (so there's nothing wrong with the device or computer), but  nothing happens when I plug it in on my desktop - the mouse works fine!

I can force with
lee@lee-desktop:~$ sudo mount /dev/sde1 /media/usbflsh
I can't eject them via nautilus, I have to umount, which only works sometimes, but I cannot write.

PLLLLLLEEEEEEEEEEEASSE help as I really need to work!!!!

PLEASE can someone with a bit of experience HELP?!!!! 

I've ran this:
lee@lee-desktop:~$ sudo blkid
/dev/sda1: LABEL="2nd1" UUID="50F45961F45949FC" TYPE="ntfs" 
/dev/sda3: LABEL="2nd2" UUID="01C6A9EAB5687100" TYPE="ntfs" 
/dev/sda5: UUID="be06f940-f320-4a71-a75a-66a367249d92" TYPE="ext4" 
/dev/sda6: UUID="5f96f190-c1c7-44db-b9c0-95f769e3b927" TYPE="swap" 
/dev/sdb1: LABEL="Windows" UUID="E434FC7334FC4A56" TYPE="ntfs" 
/dev/sdc1: LABEL="New Volume" UUID="5276E69976E67D5B" TYPE="ntfs" 
/dev/sdd1: UUID="ACA4E9EFA4E9BC48" TYPE="ntfs" 
/dev/sde1: UUID="901E-2C40" TYPE="vfat" 

The last two entries are my external HDD and USB flash drive respectively.

FStab (Which I DO NOT understand) looks like this
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=be06f940-f320-4a71-a75a-66a367249d92    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=50F45961F45949FC    /media/2nd1    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.utf8    0    0
#Entry for /dev/sda3 :
UUID=01C6A9EAB5687100    /media/2nd2    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.utf8    0    0
#Entry for /dev/sdc1 :
UUID=5276E69976E67D5B    /media/New_Volume    ntfs-3g    defaults,locale=en_GB.utf8    0    0
#Entry for /dev/sdb1 :
UUID=E434FC7334FC4A56    /media/Windows    ntfs-3g    defaults,locale=en_GB.utf8    0    0
#Entry for /dev/sdd1 :
UUID=ACA4E9EFA4E9BC48    /media/sdd1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda6 :
UUID=5f96f190-c1c7-44db-b9c0-95f769e3b927    none    swap    sw    0    0

The DVD drives are not read either :((

---

### Post by salterlee on 2011-05-16
Hi all. I upgraded to Natty (when everything was working fine) but since   then Ubuntu refuses to automatically mount USB storage devices, and  the  manual mount doesn't let me write to disk. The USB flash drive I  have  works on my Ubuntu (Natty) netbook and on my XP installation on my   desktop (so there's nothing wrong with the device or computer), but   nothing happens when I plug it in on my desktop - the mouse works fine!

I can force with
lee@lee-desktop:~$ sudo mount /dev/sde1 /media/usbflsh
I can't eject them via nautilus, I have to umount, which only works sometimes, but I cannot write.

PLLLLLLEEEEEEEEEEEASSE help as I really need to work!!!!

PLEASE can someone with a bit of experience HELP?!!!! 

I've ran this:
lee@lee-desktop:~$ sudo blkid
/dev/sda1: LABEL="2nd1" UUID="50F45961F45949FC" TYPE="ntfs" 
/dev/sda3: LABEL="2nd2" UUID="01C6A9EAB5687100" TYPE="ntfs" 
/dev/sda5: UUID="be06f940-f320-4a71-a75a-66a367249d92" TYPE="ext4" 
/dev/sda6: UUID="5f96f190-c1c7-44db-b9c0-95f769e3b927" TYPE="swap" 
/dev/sdb1: LABEL="Windows" UUID="E434FC7334FC4A56" TYPE="ntfs" 
/dev/sdc1: LABEL="New Volume" UUID="5276E69976E67D5B" TYPE="ntfs" 
/dev/sdd1: UUID="ACA4E9EFA4E9BC48" TYPE="ntfs" 
/dev/sde1: UUID="901E-2C40" TYPE="vfat" 

The last two entries are my external HDD and USB flash drive respectively.

FStab (Which I DO NOT understand) looks like this
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=be06f940-f320-4a71-a75a-66a367249d92    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=50F45961F45949FC    /media/2nd1    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.utf8    0    0
#Entry for /dev/sda3 :
UUID=01C6A9EAB5687100    /media/2nd2    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.utf8    0    0
#Entry for /dev/sdc1 :
UUID=5276E69976E67D5B    /media/New_Volume    ntfs-3g    defaults,locale=en_GB.utf8    0    0
#Entry for /dev/sdb1 :
UUID=E434FC7334FC4A56    /media/Windows    ntfs-3g    defaults,locale=en_GB.utf8    0    0
#Entry for /dev/sdd1 :
UUID=ACA4E9EFA4E9BC48    /media/sdd1    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda6 :
UUID=5f96f190-c1c7-44db-b9c0-95f769e3b927    none    swap    sw    0    0

The DVD drives are not read either :sad:(

---

### Post by howefield on 2011-05-16
Please do not spam the forum with the same question every few minutes.

Keep one thread per topic and feel free to bump once after about 24 hours has passed without reply.

Thank you.

---

### Post by salterlee on 2011-05-16
BUMP please!!!

---

### Post by pfifo on 2011-05-17
you left #ubuntu before i could give you this link.
[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/571038](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/571038)

sounds like this is caused by a bad partition table. try using fdisk or gparted to fix your partitions.

---

### Post by salterlee on 2011-05-17
Thanks pfifo - I had come across this before, but now it makes much more sense - the faulty partitions must be at the route of the problem. Will tinker (I hope without killing it) and if it solves it, will post instructions. Thanks again for your time.

---

### Post by salterlee on 2011-05-18
Just in case anyone has the same problem (and like me you get bugger all  help here apart from pfifo! Sorry, but grrr), it came down to an error in the Partition  Tables (which tell Ubuntu which drives are which), presumably caused  simply by upgrading to Natty 11) which in turn seems to have prevented  Ubuntu reading any drives properly (esp USB storage and DVDs). In the  end I had to do a fresh install (and have lost 250gigs somewhere!!!) -  there was no alternative - it's all a bit too much of a reminder of  Windows really, but I'll try to stick with it for a bit.

---

