---
title: "HELP! &quot;erased all data on entire disk&quot; with gparted from liveCD"
date: 2011-01-23
forum: General Help
---

### Post by achm on 2011-01-23
Hi,

I am in a trouble, but it should be solvable. Shouldn't it? Please...

long story short:
I deleted my hd from an ubuntu 10.10 liveCD system by trying to create a new partition table with gparted. I just wanted to restore the partition table and clicked on "create partition table" ... apply.

Now the hole hd is an unallocated file system, so without any partitions. There had been 3 ext4 partitions.

Because I did it from an liveCD, all data should be save? Is there a way to search for partitions on the hard disk and get a new old partition table and write it to the mbr?

I searched a lot already (with a very slow mobile internet connection)...

As expectable:

sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f346f

   Device Boot      Start         End      Blocks   Id  System


and:


sudo sfdisk -l /dev/sda

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0       -       0          0    0  Empty
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty


and so:

sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0


Can anyone help, please?

Nervously,
achm

---

### Post by Elfy on 2011-01-23
Stay in the livecd

[https://help.ubuntu.com/community/DataRecovery#Testdisk](https://help.ubuntu.com/community/DataRecovery#Testdisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_type_selection](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_type_selection)

good luck

---

### Post by coldraven on 2011-01-23
+1 Testdisk

---

### Post by achm on 2011-01-23
TestDisk seems to do the trick...

- it tool some time (very slow internet connection) to update the repository list (universe)
- I installed testdisk and ran it as super user
- Create - select hd - Intel - Analyse - Quick search (finds all) - no vista....

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1 14597 254 63  234516807
L Linux Swap           14598   1  1 14961 254 63    5847597
P Linux                14962   0  1 30194 254 63  244718145
P Linux                30195   0  1 38912 254 63  140054670 [ubuntu]

- ...continue - write

Then I continued with
[ MBR Code ]  Write TestDisk MBR code to first sector
Write a new copy of MBR code to first sector? (Y/N)  ...y

Now I will reboot and see what happens...


Thanks a lot!!! for the links opening my eyes!
I will report what happend.


PS: I thought testdisk would not handle ext4.

---

### Post by ronnielsen1 on 2011-01-23
> PS: I thought testdisk would not handle ext4. 	

> This new TestDisk version can undelete files for NTFS filesystem and recover deleted exFAT and ext4. 

[http://www.cgsecurity.org/wiki/TestDisk_6.11_Release](http://www.cgsecurity.org/wiki/TestDisk_6.11_Release)

---

### Post by achm on 2011-01-23
It worked!

Thanks for all your help!

:D

Now I have to make grub to find kubuntu, too. But in a new thread...

SOLVED

---

### Post by Elfy on 2011-01-23
```
sudo update-grub
``` should do that

---

