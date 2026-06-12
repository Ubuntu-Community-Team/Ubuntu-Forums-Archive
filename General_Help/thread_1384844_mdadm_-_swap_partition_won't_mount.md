---
title: "mdadm - swap partition won't mount"
date: 2010-01-18
forum: General Help
---

### Post by wsims2 on 2010-01-18
I'm running server edition 9.04 using mdadm for raid. The root partition is assembled in a raid 1 config, I have 3 drives in a raid5 config mounted at /media/raid, and the swap is in a raid 1 config. 

if i use the mount command, my swap isn't listed. the root partition and /media/raid partitions are listed. 

```
sudo mdadm --detail /dev/md1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
/dev/md1:
        Version : 00.90
  Creation Time : Sat Oct 17 08:26:08 2009
     Raid Level : raid1
     Array Size : 4891712 (4.67 GiB 5.01 GB)
  Used Dev Size : 4891712 (4.67 GiB 5.01 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Jan 18 21:52:06 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : c150dfb5:b7b90df9:3b6901bb:5699465d
         Events : 0.16

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2

```/dev/md1 is my swap partition. 

I've tried deleting the swap partition, but when i try, its always "busy".
Does it have anything to do with the line "preferred minor 1" line from the above command?

any advice?

---

