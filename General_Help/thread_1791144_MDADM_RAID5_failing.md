---
title: "MDADM RAID5 failing"
date: 2011-06-26
forum: General Help
---

### Post by bobbob1016 on 2011-06-26
[Solved (sort of)] It was a bad sata pci card, but I have a new issue, I will repost it as a new thread

Not sure why, but my mdadm RAID5 just dropped 2 drives.  I was rebuilding one of the drives (sdg1), then the second drive (sde1) dropped too.  The second one that dropped is now showing up as a spare when I do mdadm --detail /dev/md0  I would like to have some reassurance that if I readd the "spare" it won't try to resync and cause me to lose all my data.

Here is my mdadm --detail
/dev/md0:
        Version : 0.90
  Creation Time : Sun Aug 29 20:21:44 2010
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
   Raid Devices : 6
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jun 26 08:06:35 2011
          State : active, FAILED, Not Started
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 0d88f71a:0f8c6eb8:7506fbc4:05ba3487
         Events : 0.86276

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       33        1      active sync   /dev/sdc1
       2       8       17        2      active sync   /dev/sdb1
       3       0        0        3      removed
       4       0        0        4      removed
       5       8       81        5      active sync   /dev/sdf1

       6       8       65        -      spare   /dev/sde1

Edit:
Now getting that /dev/sde's superblock doesn't match the others.  I'm tempted to follow the second step here [http://ubuntuforums.org/showthread.php?t=410136](http://ubuntuforums.org/showthread.php?t=410136) but I'm not sure on the safety, nor how to repeat my exact issue in a VM to try it out without risking my data.

Here is mdadm -E /dev/sdc1 (the others are the same except sde1 which I will paste below)
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 0d88f71a:0f8c6eb8:7506fbc4:05ba3487
  Creation Time : Sun Aug 29 20:21:44 2010
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 7325679680 (6986.31 GiB 7501.50 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Sun Jun 26 08:06:35 2011
          State : clean
 Active Devices : 5
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 32dbd749 - correct
         Events : 86276

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       0        0        4      faulty removed
   5     5       8       49        5      active sync   /dev/sdd1
   6     6       8       97        6      spare   /dev/sdg1

mdadm -E /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 0d88f71a:0f8c6eb8:7506fbc4:05ba3487
  Creation Time : Sun Aug 29 20:21:44 2010
     Raid Level : raid5
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
     Array Size : 7325679680 (6986.31 GiB 7501.50 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0

    Update Time : Sun Jun 26 08:06:35 2011
          State : clean
 Active Devices : 5
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 32dbd78d - correct
         Events : 86276

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8       97        6      spare   /dev/sdg1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       0        0        4      faulty removed
   5     5       8       49        5      active sync   /dev/sdd1
   6     6       8       97        6      spare   /dev/sdg1

---

### Post by tgalati4 on 2011-06-26
RAID5 is vulnerable to rebuild failure with large drives.

---

