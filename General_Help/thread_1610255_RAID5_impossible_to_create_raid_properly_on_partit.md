---
title: "RAID5: impossible to create raid properly on partitions"
date: 2010-10-31
forum: General Help
---

### Post by miki_x on 2010-10-31
Hi,

I've tried to create a raid 5 array for the past few days and it seems impossiblet o create it properly on the right partitions.
I'm using 10.04 server, 3x 2TB Samsung F4EG (with 4k sectors that need to be properly aligned).

Here's how I proceded:
-I create a Linux raid partition on each drive with Gdisk (fdisk supporting GPT), aligned on sector 2048
-Launch mdadm to create array with:
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdd1
-I wait until the whole array is created
-I format md0 with:
mkfs.ext4 -b 4096 -E stride=16,stripe-width=32 -O extent -m 0 -v /dev/md0


The problem is that I end up with an array on the drives; not on the partitions:
my /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd[2] sdb[1] sda[0]
      3907026944 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>

```

and mdadm --detail
```
/dev/md0:
        Version : 00.90
  Creation Time : Sat Oct 30 18:11:20 2010
     Raid Level : raid5
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Oct 31 16:16:40 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 0551e0d3:44e7a9f1:46479b19:e8b0c6ac (local to host miki-server)
         Events : 0.36

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       48        2      active sync   /dev/sdd

```

I am going crazy, I've destroyed the raid 3 times (by erasing superblocks) to start over and every time I end up with a raid on the disks and not on the specified partitions.
Any help is welcome!

---

### Post by dcstar on 2010-11-01
> **miki_x said:**
> Hi,

I've tried to create a raid 5 array for the past few days and it seems impossiblet o create it properly on the right partitions.
...........
I am going crazy, I've destroyed the raid 3 times (by erasing superblocks) to start over and every time I end up with a raid on the disks and not on the specified partitions.
Any help is welcome!

Have a look at this:

[http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10)

---

### Post by miki_x on 2010-11-01
Hi,

Thanks for the link, it seems to have at least solved the raid removal issue. In fact the 3 other times I tried to remove the raid and recreate it, I was getting a raid rebuild instead of creation from scratch.
Now I'm creating the raid again from scratch, again on the right partitions as stated in /proc/mdstat:
```
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sdd1[2] sdb1[1] sda1[0]
      3907026944 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      [====>................]  resync = 22.1% (432713984/1953513472) finish=299.
6min speed=84578K/sec

unused devices: <none>

```

Since I don't want to screw up anything, here's the next steps:
-wait until finish, create mdadm.conf with the right array uuid and reboot
-create the filesystem on /dev/md0 with:
mkfs.ext4 -b 4096 -E stride=16,stripe-width=32 -m 0 -O extent -v /dev/md0

Can you confirm this is ok? Should I go for XFS instead? 

Thanks for your help!

---

### Post by miki_x on 2010-11-01
It's really driving me crazy... I went through the whole resync process (on a clean base).
I created the right "Linux Raid autodetect" partitions, everything done as mentioned in the tutorial and I end up again with the raid created on the whole disk and with md_d0p1 instead of md0.

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd[2] sdb[1] sda[0]
      3907026944 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
```

I might just give up... This is the 4th sync and it's still not working :(

---

### Post by srs5694 on 2010-11-01
My knowledge of this is limited and foggy, but I believe I've heard that at least some versions of the Linux RAID tools have problems building RAID arrays on GPT disks. You might want to investigate this aspect of it, or just convert your GPT disks to MBR disks and see if you have better luck that way.

---

### Post by miki_x on 2010-11-01
Actually the disks had an mbr partition table during the first trial...
The things is that array is built on the right partitions and can be mounted until I reboot. After that, everything gets messed up: raid on whole disks, sometimes impossible to rebuild, etc

---

