---
title: "Problem mount raid"
date: 2010-10-17
forum: General Help
---

### Post by jensws on 2010-10-17
Hello!

When i try to upgrade too ubuntu 10.10 the upgrade failed and i couldn't get the ubuntu to start again.
I installed ubuntu 10.10 on a new drive and kept my raid 1 in the computer i run ubuntu 10.04 on before uppgrade.

And now i cant mount my raid in the new system.

When i write mdadm --detail /dev/md0 i get this:


/dev/md0:
        Version : 00.90
  Creation Time : Thu Jul 22 18:28:27 2010
     Raid Level : raid1
     Array Size : 966994880 (922.20 GiB 990.20 GB)
  Used Dev Size : 966994880 (922.20 GiB 990.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Oct 17 19:51:26 2010
          State : clean, degraded, recovering
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 2% complete

           UUID : 33203dd7:d6a794ee:58dc1a0d:3a311d27
         Events : 0.337

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       2       8        2        1      spare rebuilding   /dev/sda2




I would appreciate any help or idea of my problem.
Thank you very much in advance!

---

