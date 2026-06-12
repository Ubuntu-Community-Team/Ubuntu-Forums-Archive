---
title: "64gb MicroSD only showing 30gb"
date: 2012-09-28
forum: General Help
---

### Post by TimEnid on 2012-09-28
Is there any way i can fix this? No matter how i format it, it only shows 30gb available. It previously showed 64, but now its not. Also, if i go to Disk Utility, the Drive Capacity is 30gb, but the Volume capacity is 64gb. Any suggestions?

---

### Post by Bashing-om on 2012-09-28
TimEnid; Hi !

 What does these commands tell ?:
```
sudo fdisk -lu
df -h
```
What does the device look like in GParted ?

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by TimEnid on 2012-09-28
sdl1 is the drive.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003e11c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1440002047   720000000   83  Linux
/dev/sdb2      1440004094  1465147391    12571649    5  Extended
/dev/sdb5      1440004096  1465147391    12571648   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x19ad14d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   976769023   488383488    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f891

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   976773119   488385536    7  HPFS/NTFS/exFAT

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8f3c04b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdf: 1499.7 GB, 1499651727360 bytes
255 heads, 63 sectors/track, 182322 cylinders, total 2929007280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00078baf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63  2929002929  1464501433+   7  HPFS/NTFS/exFAT

Disk /dev/sdl: 29.5 GB, 29504831488 bytes
64 heads, 32 sectors/track, 28138 cylinders, total 57626624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008806d

   Device Boot      Start         End      Blocks   Id  System

```

---

### Post by TimEnid on 2012-09-28
from df -h i get


```
tim@tim:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       686G  112G  541G  18% /
udev            5.9G  4.0K  5.9G   1% /dev
tmpfs           2.4G  1.3M  2.4G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            5.9G  884K  5.9G   1% /run/shm
/dev/sr1        198M  198M     0 100% /media/floppy0
/dev/sdf1       1.4T  685G  712G  50% /media/Buffalo 1.5tb
/dev/sda        931G  375G  510G  43% /media/Media Drive
/dev/sdc1       466G  190G  277G  41% /media/500gb Backup
/dev/sde1       932G  651G  282G  70% /media/WD
/dev/sdd1       466G  437G   30G  94% /media/500gb
```

---

### Post by TimEnid on 2012-09-28
gparted

File System: Unallocated
Size: 27.48 gb
File Sector: 0
Last sector: 57626623
Total Sectors: 57626624

---

