---
title: "Trouble mounting Maxtor external drive"
date: 2012-01-15
forum: General Help
---

### Post by lindrum on 2012-01-15
I'm having trouble mounting a Maxtor One Touch III external drive. I'm running Ubuntu 10.04.

$ sudo fdisk -l

yields:

...
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8be2f02b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS


I created a mount directory:

$ sudo mkdir /media/maxtor

then:

$ sudo mount -t ntfs /dev/sdb1 /media/maxtor

produced:

NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

Trying to mount /dev/sdb returned the same message. I'd be very grateful for any help with this!

---

### Post by coffeecat on 2012-01-15
The output of fdisk simply gives you the contents of the partition table, with no information on the state of the filesystem. The error message you get when you try to mount is significant:

> 

**NTFS signature is missing.**
Failed to mount '/dev/sdb1': Invalid argument
**The device '/dev/sdb1' doesn't seem to have a valid NTFS.**


That sounds like a damaged or missing filesystem. Since the filesystem is (or was) NTFS, what happens when you attach the drive to a Windows system?

**EDIT**: welcome to the forum!

---

### Post by lindrum on 2012-01-15
Thanks for responding. I will do that when I can, but I don't currently have a Windows machine here to try it on.

---

### Post by coffeecat on 2012-01-15
Good luck with that. If the filesystem is irretrievably damaged (let's hope not) you'll soon find out when you try to read it in Windows. If it is repairable, you're going to need Windows anyway to do a repair. NTFS is a Microsoft filesystem and there is no comprehensive Linux substitute for Windows' chkdsk (or the GUI equivalent). Ubuntu does have the Linux command line ntfsfix, but as the ntfsfix manual says:

>  ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is NOT a Linux version of chkdsk.  It only repairs some  fundamental NTFS inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS consistency check for the first boot into Windows.

---

