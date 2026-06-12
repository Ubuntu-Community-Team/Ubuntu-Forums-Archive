---
title: "I've a (fake) RAID 1 with Windows 7, need help to mount it on Ubuntu"
date: 2011-03-26
forum: General Help
---

### Post by Fentanyl on 2011-03-26
Hello, i'm using Kubuntu 10.10 and i need help to mount my RAID 1 on....
This is what i have:

- RAID 1 (2 disks 1TB/1TB ) with Windows 7 (using BIOS motherboard intel matrix storage, so i guess it's a fake raid)
      - 104Mb system reserved partition
      - 104.8Gb  NTFS (it's C on my Windows 7)
      -  895.3Gb NTFS (it's D on my Windows 7)

/dev/sdc (1 disk 750Gb with Kubuntu)

I would like to see my RAID with windows on Kubuntu.
I don't want to make mistakes and mount just one of the 2 disks of the RAID and corrupt it...

This is my sudo fdisk -l output:


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd91a0c6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12749   102296576    7  HPFS/NTFS
/dev/sda3           12749      121601   874358784    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd91a0c6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       12749   102296576    7  HPFS/NTFS
/dev/sdb3           12749      121601   874358784    7  HPFS/NTFS

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4f6602a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       90594   727690240   83  Linux
/dev/sdc2           90594       91202     4881409    5  Extended
/dev/sdc5           90594       91202     4881408   82  Linux swap / Solaris

Disk /dev/dm-0: 1000.2 GB, 1000202178560 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd91a0c6d

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/dm-0p2              13       12749   102296576    7  HPFS/NTFS
/dev/dm-0p3           12749      121601   874358784    7  HPFS/NTFS

Disk /dev/dm-1: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(335, 10, 2) logical=(120527, 49, 53)
Partition 1 has different physical/logical endings:
     phys=(327, 84, 13) logical=(234813, 237, 34)
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(119380, 132, 62)
Partition 2 has different physical/logical endings:
     phys=(256, 101, 36) logical=(153270, 41, 37)
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(364, 116, 50) logical=(113201, 29, 24)
Partition 3 has different physical/logical endings:
     phys=(372, 65, 44) logical=(147074, 114, 59)
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 101, 51) logical=(177063, 118, 26)
Partition 4 has different physical/logical endings:
     phys=(269, 114, 52) logical=(177066, 225, 63)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 104.8 GB, 104751693824 bytes
255 heads, 63 sectors/track, 12735 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 895.3 GB, 895343394816 bytes
255 heads, 63 sectors/track, 108852 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-3p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
/dev/dm-3p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-3p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-3p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


Thanks a lot in advance!!!

---

### Post by Fentanyl on 2011-03-26
anyone? :)

---

### Post by Fentanyl on 2011-03-26
This is my "cat /proc/partitions" output if can help...

major minor  #blocks  name

   8        0  976762584 sda
   8       16  976762584 sdb
   8       32  732574584 sdc
   8       33  727690240 sdc1
   8       34          1 sdc2
   8       37    4881408 sdc5
 252        0  976759940 dm-0
 252        1     102400 dm-1
 252        2  102296576 dm-2
 252        3  874358784 dm-3

---

### Post by b0b138 on 2011-03-26
You need to install dmraid. I've used it before but its been awhile, don't know much about it.

---

### Post by b0b138 on 2011-03-26
If you have it installed, look in /dev/mapper/something  You will need to mount that.

---

### Post by Fentanyl on 2011-03-26
yes, dmraid is installed by default on kubuntu.

On /dev/mapper i have

isw_eccechjbie_DanielemRaid1 
isw_eccechjbie_DanielemRaid11
 isw_eccechjbie_DanielemRaid12
isw_eccechjbie_DanielemRaid13

RAID name is DanielemRaid1

DanielemRaid11-2-3 are partitions i guess....

DanielemRaid1 points to /dev/dm-0
DanielemRaid11 points to /dev/dm-1
DanielemRaid12 points to /dev/dm-2
DanielemRaid13 points to /dev/dm-3

So, i guess i need to mount /dev/dm-2 (C on windows 7) and dm-3 (D on windows).

If so, please.. can you tell me the right command to mount these ntfs partition in READ-ONLY? so i can try without damage anything :)
Thanks in advance...

---

### Post by ronparent on 2011-03-26
b0b138 has it nailed about dmraid. Although dmraid is on the cd it is not automatically installed if 10.10 is not installed to a raid. Once dmraid is installed the raid partitions will automatically show up in Nautilus and are mountable with no extra steps. In earlier editions you did have to separately mount them to get access.

---

### Post by Fentanyl on 2011-03-26
> **ronparent said:**
> b0b138 has it nailed about dmraid. Although dmraid is on the cd it is not automatically installed if 10.10 is not installed to a raid. Once dmraid is installed the raid partitions will automatically show up in Nautilus and are mountable with no extra steps. In earlier editions you did have to separately mount them to get access.

I don't have nautilus, i'm using kubuntu so i don't have nautilus installed but i've dolphin.
I see dmraid is installed and all i have is what i wrote on my previous message :(

---

### Post by ronparent on 2011-03-26
> On /dev/mapper i have

isw_eccechjbie_DanielemRaid1 
isw_eccechjbie_DanielemRaid11
isw_eccechjbie_DanielemRaid12
isw_eccechjbie_DanielemRaid13

RAID name is DanielemRaid1

DanielemRaid11-2-3 are partitions i guess....

DanielemRaid1 points to /dev/dm-0
DanielemRaid11 points to /dev/dm-1
DanielemRaid12 points to /dev/dm-2
DanielemRaid13 points to /dev/dm-3

All of the above are symbolic links that can be used to mount the partitions. Raid1 represents the raid array itself and is not mountable. The three that follow it are the partitions.

---

### Post by ronparent on 2011-03-26
I see that we are cross posting. 

ie sudo **mount /dev/mapper/isw_eccechjbie_DanielemRaid12 /mnt** or
**sudo mount /dev/dm-2 /mnt**

You can specify an ntfs parameter or read only parameter but not absolutely necessary. What is necessary is that the file location you want to mount to exists (/mnt does in ubuntu).

---

### Post by Fentanyl on 2011-03-26
> **ronparent said:**
> All of the above are symbolic links that can be used to mount the partitions. Raid1 represents the raid array itself and is not mountable. The three that follow it are the partitions.

Good... so i need to mount /dev/dm-x (1-2 or 3) right?
I'll create 2 folders, for example C and D in my home dir
/home/fentanyl/C and /home/fentanyl/D

I know, i'm a newbie :)
Which is the correct line to add to fstab?

/dev/dm-1   /home/fentanyl/C  ntfs....and then? :(
Sorry tried to search on google but i'm pretty confused :)

---

### Post by ronparent on 2011-03-26
Try **sudo mount /dev/dm-1 /home/fentanl/C**

Make a **/home/fentanl/C** before you try mounting to it. When it works add it to fstab in the same form with whatever parameters you want to use.

---

### Post by Fentanyl on 2011-03-26
> **ronparent said:**
> Try **sudo mount /dev/dm-1 /home/fentanl/C**

Make a **/home/fentanl/C** before you try mounting to it. When it works add it to fstab in the same form with whatever parameters you want to use.

Thank you very much! all done and everything works fine :)

---

### Post by ronparent on 2011-03-27
It's been my pleasure. An easy problem and a savy poster.

---

