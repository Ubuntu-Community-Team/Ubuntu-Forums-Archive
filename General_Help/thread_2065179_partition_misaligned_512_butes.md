---
title: "partition misaligned 512 butes"
date: 2012-10-01
forum: General Help
---

### Post by daveglasgow70 on 2012-10-01
I am trying to install a software (RAID 5) and formatted my disks to  unallocated to allow Unbuntu to format them during th building of the  array.

After Unbuntu forms the array ,one of my drives (Western Digital) ST2000DM001-9YN164) is giving a warning that thedrive is mis-aligned and is suggesting I repartition.

I have tried to use gparted to resolve the issue. It seems to only allow the partition ton be shifter by 1M increments and 0.5 for 512 bytes is not an option.

I have included drive info below. The four raid elements I intend to use are sda1 through sdb1

sudo doneill@server:~$ sudo fdisk -lu
[sudo] password for doneill: 

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000abb64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  3907024064  1953512001   fd  Linux RAID autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009d028

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux RAID autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002afc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  3907024064  1953512001   fd  Linux RAID autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eaf5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  3907024064  1953512001   fd  Linux RAID autodetect

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005dee9

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   482369535   241183744   83  Linux
/dev/sde2       482371582   488396799     3012609    5  Extended
/dev/sde5       482371584   488396799     3012608   82  Linux swap / Solaris

Disk /dev/md0: 6000.8 GB, 6000784441344 bytes
2 heads, 4 sectors/track, 1465035264 cylinders, total 11720282112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 1048576 bytes / 3145728 bytes
Alignment offset: 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
doneill@server:~$ sudo fdisk -lu > output
Disk /dev/md0 doesn't contain a valid partition table

Is anyone able to point me in the right dircetion?

Thanks.

---

