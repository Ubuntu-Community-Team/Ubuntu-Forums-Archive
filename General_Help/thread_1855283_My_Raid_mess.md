---
title: "My Raid mess"
date: 2011-10-05
forum: General Help
---

### Post by skaramanger on 2011-10-05
Greetings,

I have been reviewing, threads regarding raid and am not finding my problem.  I'm using raid1 one as a non-system setup for storage and redundency.

Recently, I got a degraded array email about one of my disks /dev/sda.  So I attempt to check it out.  To make a long story short, out of ignorance and impatience (except I have backups of most of my data)I blew away the old raid.  Created new single partitions on each 1TB Samsung and created created a reiserfs partition on /dev/md0.  Presently, I'm getting conflicting/confusing messages when I attempt to verify that my array is sync'ing.  So I have included below all relevant data that I hope will help in solving my problem.

```
~$ sudo fdisk -l 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x35a3fa56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3a5abcc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2432    19535008+  83  Linux
/dev/sdc2            2433       22796   163573830    5  Extended
/dev/sdc3           22797       24028     9888768   82  Linux swap / Solaris
/dev/sdc4           24028       30402    51200000   83  Linux
/dev/sdc5            2433        6404    31898400+  83  Linux
/dev/sdc6            6404       22796   131674112   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001    5  Extended
/dev/sdd5               1      121601   976759969+  83  Linux

Disk /dev/md_d0: 1000.2 GB, 1000204795904 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x35a3fa56

      Device Boot      Start         End      Blocks   Id  System
/dev/md_d0p1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 1000.2 GB, 1000204795904 bytes
2 heads, 4 sectors/track, 244190624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


```

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb[0]
      976762496 blocks [2/1] [U_]
      
md_d0 : active (auto-read-only) raid1 sda[1]
      976762496 blocks [2/1] [_U]
      
unused devices: <none>


```

I somehow have two raid-1 arrays now.  I know I screwed up somewhere, but I'm not sure.  I need to walk back from here.  I just did a restore to my mounted rw raid, I'll take that to mean md0, md_d0 has got me confused.  I'll wait for some advice here before I attempt to make any further changes.

Tia

---

### Post by blueridgedog on 2011-10-06
I assume you want to make a raid partition out of sda1 and sdb1 (to be created).  Correct?  Or are you trying to make sda1 and sdd5 into a raid?

You currently have two raid devices created:

/dev/md_d0
/dev/md0

To determine their membership, what is the output of:

```
sudo mdadm --detail /dev/md0
```

and 

```
sudo mdadm --detail /dev/md_d0
```

???  Do you have the members of md0 that you want?

If you want to remove md_d0, then

```
sudo mdadm --stop /dev/md_d0
sudo mdadm --remove /dev/md_d0
```

If you find that you want sdd5 a part of md0 and it is not:

```
mdadm --add /dev/md0 /dev/sdd5
```

If you want to make a partition on sdb (sdb1), then make it with fdisk, then add it as above, but using sdb1 as the target.

In the end you should have only one mdn device and the drives you want inside the array.  You may have to format the new partition and restore your data.

---

### Post by skaramanger on 2011-10-06
blueridgedog,


> **blueridgedog said:**
> I assume you want to make a raid partition out of sda1 and sdb1 (to be created).  Correct? 
Yup
> Or are you trying to make sda1 and sdd5 into a raid?
sdd5 is my backup medium
> You currently have two raid devices created:
/dev/md_d0
/dev/md0
To determine their membership, what is the output of:
```
sudo mdadm --detail /dev/md0
```


```
 sudo mdadm --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Wed Sep 14 01:16:51 2011
     Raid Level : raid1
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Oct  6 21:19:27 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 4f51d3f1:d5435c42:7f8c214b:6ff7bdb8
         Events : 0.6197

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8        0        1      active sync   /dev/sda


```

> 
and 

```
sudo mdadm --detail /dev/md_d0
```

This was gone after repartitioning sda and sdb and a reboot

> ???  Do you have the members of md0 that you want?

Yes now I do.:)

>  If you want to remove md_d0, then
```
sudo mdadm --stop /dev/md_d0
sudo mdadm --remove /dev/md_d0
```
If you find that you want sdd5 a part of md0 and it is not:
```
mdadm --add /dev/md0 /dev/sdd5
```
It went away with a reboot, but I did think I tried the above and got an error message with respect to it not being active to begin with.
>  If you want to make a partition on sdb (sdb1), then make it with fdisk, then add it as above, but using sdb1 as the target.
In the end you should have only one mdn device and the drives you want inside the array.  You may have to format the new partition and restore your data.

Yeah we're good now.  Thanks for your reply.  It took awhile, but I did figure it out.  I rebooted and made sure the that both drives had good partitions type linux raid. I then added /dev/sdb to the array /dev/md0

```
 sudo mdadm /dev/md0 --add /dev/sdb 
```
```
 sudo mdadm --assemble --scan 
```
```
 sudo mkfs.reiserfs /dev/md0 
```
I thought I wanted xfs, Is that better for large files like wavs and ISOs than reiserfs.

The raid is fully sync'd now :).  I'm going to let is "soak" in for while before I start doing a complete restore or open a vm stored on it.

I guess my confusion arose from the fact that when you assemble an array with more than one device, which one is the main disk and which one is th e mirror is not clear particularly from the man page.  When attempting to try and access sda when the array was degraded, I'd get a device busy error message.  That was it was still part of the array, even after I had stopped the array? Should I have been able to use the remove switch for the main disk of the array?  I have searched the 'net for tutorials and mostly its sketchy with solutions for specific problems.  This is only a storage array, I'd like to have been able to not use dos partitioning, but that is all cfdisk/fdisk permit? AFAIK i.e.

Well thanks again

---

### Post by kuchera68 on 2011-10-07
> **skaramanger said:**
> blueridgedog,
I guess my confusion arose from the fact that when you assemble an array with more than one device, which one is the main disk and which one is th e mirror is not clear particularly from the man page.  When attempting to try and access sda when the array was degraded, I'd get a device busy error message.  That was it was still part of the array, even after I had stopped the array? Should I have been able to use the remove switch for the main disk of the array? 


This behavior caught me off guard as well. I was just trying to test my raid1 array by pulling a disk. Ubuntu would not boot up and load the degraded array. I tried to manually assemble the array with one disk and got the device busy error as well. I finally found out that my raid array /dev/md0 was assembled, but set as inactive. To solve this I had to stop the array and then reasseble. It found just the single drive and I was able to access my data. Not the best solution, but it works.

My whole problem solving process is spelled out in the post: [http://ubuntuforums.org/showthread.php?t=1855425](http://ubuntuforums.org/showthread.php?t=1855425)

---

