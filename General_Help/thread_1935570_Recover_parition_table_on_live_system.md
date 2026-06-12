---
title: "Recover parition table on live system"
date: 2012-03-04
forum: General Help
---

### Post by thelamer on 2012-03-04
So after a series of whoops I have nuked the partition table of my system disk. The thing is the system is online and all 3 partitions are mounted right now. 

I am not concerned with data loss as I have allready made a file backup of the partitions to another server. It seems like the system has to have the origional table stored somewhere in order to be online and have everything mounted properly, and I should just be able to dump that and restore it. 

Actually using testdisk and gpart is what further nuked my disk so I don't think those utilities can help me much anymore. 


So what I have right now is: 

```
/dev/sdb3 on / type ext4 (rw,errors=remount-ro,commit=0)
/dev/sdb2 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```


And no defined partitions in fdisk: 

```
sfdisk -d /dev/sdb
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=        0, size=        0, Id= 0
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

```

Anyone got any ideas?

---

### Post by oldfred on 2012-03-04
Do you have any backups of partition table from sfdisk, fdisk or boot info script?

I run boot info script as part of my rsync backup just to have current documentation of my system.

Are you sure testdisk does not find anything. It is good at finding old partitions info.

[http://www.win.tue.nl/~aeb/partitions/partition_tables-2.html#ss2.7](http://www.win.tue.nl/~aeb/partitions/partition_tables-2.html#ss2.7)
All partition table sectors must have the 55, AA signature

One advantage of the new gpt partitioning is that it keeps a backup of the partition table.

---

### Post by thelamer on 2012-03-04
Testdisk finds an old partition block for my now resized windows 7 install. So I did the quick scan and applied changes then when trying to add the last linux parition (/dev/sdb3) I realized the size was off. So I am at the point now where any "recovery" tool is probally not a good option. I mean I have the disk information as it is mounted. 

Can I use /proc/partitions? Or something similar to regenerate the table? 

```
cat /proc/partitions 
major minor  #blocks  name

   8        0  976762584 sda
   8        1  976761560 sda1
   8       16  976762584 sdb
   8       17     102400 sdb1
   8       18  317426688 sdb2
   8       19  659231744 sdb3

```

---

### Post by oldfred on 2012-03-04
You still are missing the start points.

This is my system.

```
fred@fred-LT-A105:~$ cat /proc/partitions 
major minor  #blocks  name

   8        0  156290904 sda
   8        1   56797776 sda1
   8        2   30716280 sda2
   8        3          1 sda3
   8        5   15358108 sda5
   8        6    3068383 sda6
   8        7   50090638 sda7
fred@fred-LT-A105:~$ sudo sfdisk -d /dev/sda
[sudo] password for fred: 
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=113595552, Id= 7, bootable
/dev/sda2 : start=113595615, size= 61432560, Id= 7
/dev/sda3 : start=175028236, size=137034389, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=175028238, size= 30716217, Id=83
/dev/sda6 : start=205744518, size=  6136767, Id=82
/dev/sda7 : start=211881348, size=100181277, Id=83
fred@fred-LT-A105:~$ sudo fdisk -lu

Disk /dev/sda: 160 GB, 160039272960 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312576705 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   113595614    56797776    7  HPFS/NTFS
/dev/sda2       113595615   175028174    30708247    7  HPFS/NTFS
/dev/sda3       175028236   312062624    68509192    5  Extended
/dev/sda5       175028238   205744454    15350107   83  Linux
Warning: Partition 5 does not end on cylinder boundary.
/dev/sda6       205744518   211881284     3060382   82  Linux swap
Warning: Partition 6 does not end on cylinder boundary.
/dev/sda7       211881348   312062624    50082637   83  Linux
Warning: Partition 7 does not end on cylinder boundary.
fred@fred-LT-A105:~$ 


```

Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

Gparted now has some repair tools also. May just be like testdisk?
GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted


Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

Note: this is all over my head, some of those who really know partitions have not been in forum for quite a while.

---

