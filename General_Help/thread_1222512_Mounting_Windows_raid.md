---
title: "Mounting Windows raid"
date: 2009-07-25
forum: General Help
---

### Post by rathje40 on 2009-07-25
I have a Dell Dimension 9200 with 2x250GB raid-0.  The raid has XP factory installed, but it can't boot due to a dll corruption.  I desperately need to be able to get to the existing data on the drive, so I'm trying to use a cdrom-based ubuntu to access it.  I came across <http://ubuntuforums.org/showthread.php?t=833653>.  Unfortunately, my system is somewhat different than the one described by [Martigen]("http://ubuntuforums.org/member.php?u=322590").  While /dev/sda has partitions, /dev/sdb doesn't.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       60374   484897927+   7  HPFS/NTFS
/dev/sda3           60375       60787     3317422+  db  CP/M / CTOS / ...

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52de52dd

Disk /dev/sdb doesn't contain a valid partition table

ubuntu@ubuntu:~$ cat /proc/partitions
major minor  #blocks  name

   7        0     691260 loop0
   8        0  244140625 sda
   8        1      56196 sda1
   8        2  244084397 sda2
   8       16  244140625 sdb

I tried:
ubuntu@ubuntu:~$ sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sda /dev/sdb
mdadm: array /dev/md0 built and started.

Now the fdisk also shows:

Disk /dev/md0: 499.9 GB, 499999965184 bytes
255 heads, 63 sectors/track, 60788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1           7       56196   de  Dell Utility
/dev/md0p2   *           8       60374   484897927+   7  HPFS/NTFS
/dev/md0p3           60375       60787     3317422+  db  CP/M / CTOS / ...

and /proc/partitions shows:

   9        0  488281216 md0
 259        0      56196 md0p1
 259        1  484897927 md0p2
 259        2    3317422 md0p3

Unfortunately:

ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/md0p2 /mnt
NTFS signature is missing.
Failed to mount '/dev/md0p2': Invalid argument
The device '/dev/md0p2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

Help!

---

