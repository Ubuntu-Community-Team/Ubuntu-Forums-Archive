---
title: "Easy questions about MDADM on raid5"
date: 2011-06-16
forum: General Help
---

### Post by McManCSU on 2011-06-16
The problem is that I have a faulty drive and it has gotten to the point now where the drive is legitimately having problems and mdadm doesn't like to start from a cold start without manual assembly.  I realize I need to replace it which is fine, but I have years of data on the device so naturally I am a little hesitant to just play around with array.

```
# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Tue Apr 10 21:24:36 2007
     Raid Level : raid5
     Array Size : 1465159488 (1397.29 GiB 1500.32 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jun 15 22:13:09 2011
          State : clean, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : c89f4729:ad98c8f9:a854c56d:a19caf8b
         Events : 0.1586595

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       0        0        2      removed
       3       0        0        3      removed

       4       8       64        -      spare   /dev/sde
       5       8       48        -      faulty spare   /dev/sdd
root@MediaMadness:/opt# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb[0] sde[4](S) sdd[5](F) sdc[1]
      1465159488 blocks level 5, 64k chunk, algorithm 2 [4/2] [UU__]

unused devices: <none>
```Questions:
1) When I replace the drive, do I need to get the same size?  ie 500GB, or can I increase it?  I am not sure what the raid algorithm does for non-uniformly sized disks...
2) For now, I am unable to write to the array (maybe unrelated, but I am not sure).  If I remove the faulty drive right now, will the array still work alright for normal use (at least reading), I mean will I be able to restart the array with one disk missing?  I realize raid 5 has a single spare, so I would hope the spare would take over in the mean time which I wait for the replacement.

Thanks!

---

### Post by McManCSU on 2011-06-16
Bump

---

