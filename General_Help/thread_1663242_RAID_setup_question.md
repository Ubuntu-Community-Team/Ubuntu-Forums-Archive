---
title: "RAID setup question"
date: 2011-01-09
forum: General Help
---

### Post by kravitz999 on 2011-01-09
I'm trying to setup a RAID 5 array of 3x2TB drives and noticed that, besides having a faulty drive listed, i keep getting what looks like two separate arrays defined.  I've setup the array using the following :[INDENT][FONT=Courier New][SIZE=1]sudo mdadm --create /dev/md01 --verbose --chunk=64 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sde
[/SIZE][/FONT][/INDENT]So I've defined it as md01, or so I think.  However, looking in the Disk Utility the array is listed as md1 (degraded) instead.  Sure enough I get :[INDENT][FONT=Courier New][SIZE=1]cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sde[3](F) sdc[1] sdb[0]
      3907028992 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_][/SIZE][/FONT]
[/INDENT]So i tried getting info from mdadm on both md01 and md1 :[INDENT][FONT=Courier New][SIZE=1]user@al9000:~$ sudo mdadm --detail /dev/**md1**
/dev/md1:
        Version : 00.90
  Creation Time : Sun Jan  9 10:51:21 2011
     Raid Level : raid5
     Array Size : 3907028992 (3726.03 GiB 4000.80 GB)
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Jan  9 10:55:25 2011
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : d4f06e33:0b7841a2:1f7eaf27:9856d476 (local to host al9000)
         Events : 0.12

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       0        0        2      removed

       3       8       64        -      faulty spare   /dev/sde
user@al9000:~$ sudo mdadm --detail /dev/**md01**
/dev/md01:
        Version : 00.90
  Creation Time : Sun Jan  9 10:51:21 2011
     Raid Level : raid5
     Array Size : 3907028992 (3726.03 GiB 4000.80 GB)
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Jan  9 10:55:41 2011
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : d4f06e33:0b7841a2:1f7eaf27:9856d476 (local to host al9000)
         Events : 0.14

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       0        0        2      removed

       3       8       64        -      faulty spare   /dev/sde
[/SIZE][/FONT][/INDENT]Is this normal? I've tried using mdadm to --stop then --remove both arrays and then start from scratch but I end up in the same place.  I'm just getting my feet wet with this so perhaps I'm missing some fundamentals here...

I think the drive fault is a separate issue, strange since the Disk Utility says the drive is healthy and i'm running the self test now.  Perhaps a bad cable is my next check...

---

### Post by kidders on 2011-01-10
Hi there,

Why not stick with the standard nomenclature? If you're defining two arrays, you should call them md0 and md1, rather than (a pretty ambiguous) md01 and md1.

Assuming there's no useful data on your array, I'd suggest starting from scratch, and destroying any RAID/filesystem headers on /dev/sdb, /dev/sdc, and /dev/sde with dd. That way, you can avoid confusion that might arise out of mdadm detecting old superblocks from prior attempts to create an array. For example, the disk you're suspicious of may simply have been previously *tagged* as faulty for some reason ... It could well be just fine.

I hope that helps.

---

### Post by kravitz999 on 2011-01-10
Great thanks for the help!  I tried once to tear down the array and start from scratch already, deleting and repartitioning all the drives etc. but I'm nt sure how to destroy the RAID/filesystem headers as you suggest.  I thought deleting and then recreating the partitions would have fixed that....

And regarding the use of multiple arrays with non standard nomenclature, I guess thats the meat of my confusion - i only ever setup *ONE array* (/dev/md01) and then the second (/dev/md1) shows up for reasons unknown.  Granted, I should have used 'md0' to start but I'm not sure how 'md1' ever came into play.  Is there anything Ubuntu does in the background that would have caused this?

And how would you go about removing the faulty 'tag' of the drive?

---

### Post by kidders on 2011-01-11
> **kravitz999 said:**
> I thought deleting and then recreating the partitions would have fixed that.Not really... If you're adding /dev/sdc (for example) to an array, as opposed to /dev/sdc2 (for example), partitioning is not really relevant. In any case, repartitioning a disk rarely alters more than a few hundred of bytes ... Nothing gets deleted.

To *really* kill old partiton tables, filesystem/RAID superblocks, etc. you can overwrite the first few megabytes of a disk with garbage from /dev/zero or /dev/urandom. The "dd" utility is the handiest way of doing it quickly/painlessly, but be careful ... accidentally dumping garbage data onto the wrong disk would do tremendous damage!

> **kravitz999 said:**
> Is there anything Ubuntu does in the background that would have caused this?My guess is that some bits figure md01 = md1, while other bits don't see them as the same thing.

---

