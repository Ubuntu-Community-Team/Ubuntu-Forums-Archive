---
title: "mounting a filesystem"
date: 2011-02-04
forum: General Help
---

### Post by Zaid on 2011-02-04
Having trouble mounting a filesystem , I created a software raid system on it and it worked fine and then I restarted it wouldn't auto-mount so I did it by hand , and now I get this : 

> sudo mount -t ntfs-3g /dev/md0 /mnt/BattleShip 
NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

> nick@Linux:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe697f35a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ce60c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004ad19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       58507   469954560   83  Linux
/dev/sdc2           58507       60802    18428929    5  Extended
/dev/sdc5           58507       60802    18428928   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014d71

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/md0: 2000.4 GB, 2000404086784 bytes
2 heads, 4 sectors/track, 488379904 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Any ideas ?

---

### Post by Zaid on 2011-02-04
I tried this command :
> 
sudo fdisk -l -u /dev/md0


and got this : 

> 
Disk /dev/md0: 2000.4 GB, 2000404086784 bytes
2 heads, 4 sectors/track, 488379904 cylinders, total 3907039232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


On a worst case scenario is there at least anyway to recover the data ? I could just remake the array...

---

### Post by Zaid on 2011-02-05
Anyone ? I've searched the Internet and there are alot of people with this problem but no solutions or why it happens.... I was able to mount it at every boot before I got this error.

---

### Post by Zaid on 2011-02-05
bump , if no one knows the answer can this please be moved into the right category ?

---

### Post by Zaid on 2011-02-07
Bump

---

