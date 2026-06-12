---
title: "mdadm RAID-6 questions: Chunk Size and LVM"
date: 2011-05-20
forum: General Help
---

### Post by manders2600 on 2011-05-20
I am attempting to set up an Ubuntu Desktop system to use as a home file server, primarily for media (music and video).  I will be using RAID-6 on 8 physical drives (2TB Hitachi Deskstar, 64MB cache, SATA III).  The effective storage space will be 12TB (4TB used for parity).

I have installed natty via the alternate install usb stick, set up LVM on the Seagate 1TB (non-RAID) I am using to hold the OS, and subsequently followed this guide: [http://ubuntuforums.org/showthread.php?t=1663597](http://ubuntuforums.org/showthread.php?t=1663597) basically to the letter.

**[COLOR="Blue"]Primary Concern[/COLOR]**
I have gotten as far as "Let's create a volume", which I have completed, and I am currently waiting as the array re-syncs.

However, the output I get from:
```
mdadm --query --detail /dev/md0
```
is different than what is shown in the tutorial in the areas:

1. The chunk size is listed as 512K, as opposed to 128K
2. There is an entry directly above the "chunk size" which reads: "Layout : left-symmetric"
3. Thee is no "Preferred minor:" entry below the "Total devices: entry.

Here is my output:
```
root@marks-server:~# mdadm --query --detail /dev/md0 
/dev/md0: 
        Version : 1.2 
  Creation Time : Thu May 19 20:48:06 2011 
     Raid Level : raid6 
     Array Size : 11721071616 (11178.09 GiB 12002.38 GB) 
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB) 
   Raid Devices : 8 
  Total Devices : 8 
    Persistence : Superblock is persistent 
 
    Update Time : Fri May 20 11:09:10 2011 
          State : active, resyncing 
 Active Devices : 8 
Working Devices : 8 
 Failed Devices : 0 
  Spare Devices : 0 
 
         Layout : left-symmetric 
     Chunk Size : 512K 
 
 Rebuild Status : 47% complete 
 
           Name : marks-server:0  (local to host marks-server) 
           UUID : d09798b3:7c22beff:d2f44ee6:dd1d3c07 
         Events : 8 
 
    Number   Major   Minor   RaidDevice State 
       0       8       17        0      active sync   /dev/sdb1 
       1       8       33        1      active sync   /dev/sdc1 
       2       8       49        2      active sync   /dev/sdd1 
       3       8       65        3      active sync   /dev/sde1 
       4       8       81        4      active sync   /dev/sdf1 
       5       8       97        5      active sync   /dev/sdg1 
       6       8      113        6      active sync   /dev/sdh1 
       7       8      129        7      active sync   /dev/sdi1

```

And the output from the original tutorial:
```
sudo mdadm --query --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Fri Jan  7 15:29:35 2011
     Raid Level : raid6
     Array Size : 7814053376 (7452.06 GiB 8001.59 GB)
  Used Dev Size : 1953513344 (1863.02 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jan  9 18:38:21 2011
          State : active, resyncing
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 128K

 Rebuild Status : 47% complete

           UUID : 8fe9e130:be7c000c:2e28bbcb:f6848a15
         Events : 0.9

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       5       8       81        5      active sync   /dev/sdf1
```

I believe the third difference, and possibly the second, might be benign, but I wonder about the chunk size difference.

I created the volume immediately after creating the array in the instructed manner, and I am wondering if I should have waited for the array to re-sync first?  Also, when originally issuing the command to create the array:
```
sudo mdadm --create --verbose /dev/md0 --level=6 --raid-devices=8 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1
```
I receive the following output:
```
mark@marks-server:~$ sudo mdadm --create --verbose /dev/md0 --level=6 --raid-devices=8 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1 
mdadm: layout defaults to left-symmetric 
mdadm: chunk size defaults to 512K 
mdadm: layout defaults to left-symmetric 
mdadm: layout defaults to left-symmetric 
mdadm: layout defaults to left-symmetric 
mdadm: layout defaults to left-symmetric 
mdadm: layout defaults to left-symmetric 
mdadm: layout defaults to left-symmetric 
mdadm: layout defaults to left-symmetric 
mdadm: layout defaults to left-symmetric 
mdadm: layout defaults to left-symmetric 
mdadm: size set to 1953511936K 
mdadm: Defaulting to version 1.2 metadata 
mdadm: array /dev/md0 started. 
```

This output seems to suggest that both items (1 and 2) of concern are defaults, and I am wondering if there is an option to change these, and if so, what it would be?

**[COLOR="blue"]Secondary Issue[/COLOR]**

I would like to partition this RAID aray, once it is set up, using LVM, in order to easily resize and change partitions easily and as needed.  I have already partitioned my OS drive using LVM, and it seems to work well.  However, I would like to ensure that when doing this on my RAID array, I am not becoming misaligned.  My assumption would be that, since the drives themselves are already aligned, the LVM logical volumes within the logical volume group would be aligned as long as each partition contained an even number of MB, so that every lvm partition would be some multiple of 102,400 (and thus 4,096) bytes.

I wonder, though, if there needs to be some offset created with lvm partitions on their own?

Thanks in advance to anyone taking the time to read and help out,

Mark

---

