---
title: "RAID6 build problem"
date: 2010-05-30
forum: General Help
---

### Post by srengr on 2010-05-30
I installed 10.04 on a new machine and 'tried' to create a 4 disk RAID6 array on four new 4TB drives.

The build seemed to go fine, but a check on the new dev shows the following:

/dev/md0:
        Version : 00.90
  Creation Time : Sun May 30 21:53:11 2010
     Raid Level : raid6
     Array Size : 3906975616 (3725.98 GiB 4000.74 GB)
  Used Dev Size : 1953487808 (1862.99 GiB 2000.37 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun May 30 21:59:20 2010
          State : clean, degraded, resyncing
 Active Devices : 0
Working Devices : 0
 Failed Devices : 4
  Spare Devices : 0

     Chunk Size : 64K

 Rebuild Status : 0% complete

    Number   Major   Minor   RaidDevice State
       7       8       17        0      faulty spare rebuilding   /dev/sdb1
       6       8       33        1      faulty spare rebuilding   /dev/sdc1
       5       8       49        2      faulty spare rebuilding   /dev/sdd1
       4       8       65        3      faulty spare rebuilding   /dev/sde1

What the heck does 'faulty spare rebuilding' on all devs mean?  Will it rebuild and sync, or do I need to do something?

Thanks,

srengr

---

### Post by srengr on 2010-06-01
Well, thanks for all the helpful hints.  I figured it out on my own.  

I had to wipe the drives with dd and start over creating the array.  Looks like some existing metadata on the drives was messing up mdadm.  I also built the new array with the --metadata 1.2 switch.  Ubuntu defaults to metadata version 0.90 (the net gurus recommend using the latest version).

--srengr

---

