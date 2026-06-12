---
title: "Dissapeared drives!"
date: 2006-01-23
forum: General Help
---

### Post by patrickfromspain on 2006-01-23
Hi there! 

I've got a very odd problem. I've installed Dapper on another partition to try, and I think that since I'm using it I have this problem:

First off, I don't know if it's Dapper's fault, let's see. In dapper I've set my other partitions to mount as they did in breezy. sda1 for read only with all user access and sda5 for read and write for all users. I also automount sda7 (breezys partition). Well.. all works fine in dapper BUT not in breezy. In breezy, if I go to the places menu none of my partitions are shown up. If in the same menu I go to My PC (I don't know who it's called in english) I can see the floppy, the dvd writer, the dvd reader and my filesystem, but... Where are sda1, sda5 and sda8 (dapper's partition)?? Also in my desktop they have disappeared. If I go to /media/sda5 or /sda1 I can write to sda5 and read from sda1. I haven't done anything in breezy to mess that, and don't know if something in dapper has changed something...

Any ideas?

---

### Post by dcstar on 2006-01-23
[QUOTE=patrickfromspain]Hi there! 

I've got a very odd problem. I've installed Dapper on another partition to try, and I think that since I'm using it I have this problem:

First off, I don't know if it's Dapper's fault, let's see. In dapper I've set my other partitions to mount as they did in breezy. sda1 for read only with all user access and sda5 for read and write for all users. I also automount sda7 (breezys partition). Well.. all works fine in dapper BUT not in breezy. In breezy, if I go to the places menu none of my partitions are shown up. If in the same menu I go to My PC (I don't know who it's called in english) I can see the floppy, the dvd writer, the dvd reader and my filesystem, but... Where are sda1, sda5 and sda8 (dapper's partition)?? Also in my desktop they have disappeared. If I go to /media/sda5 or /sda1 I can write to sda5 and read from sda1. I haven't done anything in breezy to mess that, and don't know if something in dapper has changed something...

Any ideas?[/QUOTE]
What is in your Breezy /etc/fstab file?

---

### Post by patrickfromspain on 2006-01-24
[QUOTE=dcstar]What is in your Breezy /etc/fstab file?[/QUOTE]

here it is:

# <file system> <mount point>   <type>       <options>       <dump>  <pass>
proc            /proc           proc         defaults          0       0
/dev/sda7       /               reiserfs     notail            0       1
/dev/sda1       /media/sda1     ntfs         ro,user,auto,umask=0 0 0
/dev/sda5       /media/sda5     vfat         rw,user,auto,umask=0 0 0
/dev/sda8	/media/sda8	ext3         rw,user,auto      
/dev/sda6       none            swap         sw                0       0
/dev/hdb        /media/cdrom0   udf,iso9660  user,noauto       0       0
/dev/hda        /media/cdrom1   udf,iso9660  user,noauto       0       0
/dev/fd0        /media/floppy0  auto         rw,user,noauto    0       0

I don't see anything special, I think all is fine.

My dapper one looks like this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc                  defaults        0       0
/dev/sda8       /               ext3                 defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs         ro,user,auto,umask=0 0 0
/dev/sda5       /media/sda5     vfat         rw,user,auto,umask=0 0 0
/dev/sda7       /media/sda7     reiserfs    defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Any ideas?

Edit: I've tried comenting out the lines referring to sda1, sda5 and sda7 in dapper's fstab, rebooting into dapper, and then reboting into breezy.. still the same problem. Also, I am running in breezy now, and the mtab also seems fine, and sda1, sda5 and sda8 appear as mounted:

/dev/sda7 / reiserfs rw,notail 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-k7/volatile tmpfs rw,mode=0755 0 0
/dev/sda1 /media/sda1 ntfs ro,noexec,nosuid,nodev,umask=0 0 0
/dev/sda5 /media/sda5 vfat rw,noexec,nosuid,nodev,umask=0 0 0
/dev/sda8 /media/sda8 ext3 rw,noexec,nosuid,nodev 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

---

### Post by patrickfromspain on 2006-01-24
Just a short thing: the same thing that's happening in breezy, is now happening in dapper, after an update.

---

### Post by patrickfromspain on 2006-01-25
Up! Nobody has a clue on how to solve this??

---

### Post by yostral on 2006-04-27
Hello.

I can't help you (I don't know if it's resolved or not).
But I have the same problem : all my drives appear on my Breezy, it was fine at the beginning too with the dapper, but after an update (in january or february), no more drives icons (exept DVD drive and /)... I can still mount them manually.

If I remove "noauto" option in fstab, it appears...

Does someone know how to solve it?

---

### Post by Norppa on 2006-04-27
Same here. I have two partitions that I have to manually mount after starting Ubuntu. When I restart, they disappear. What to do? By manually I mean I do it through System -> Admin -> Drives (I have the Finnish version, so I'm not sure if this is the correct translation, but anyway...). Is there a better way to mount the partitions? Please help!


*UBUNTU - hmmm, maybe there is something... great...*

---

### Post by yostral on 2006-04-27
I think it's a bug. Go to see this thread : [http://ubuntuforums.org/showthread.php?t=166445](http://ubuntuforums.org/showthread.php?t=166445)

---

