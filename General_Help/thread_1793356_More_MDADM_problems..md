---
title: "More MDADM problems."
date: 2011-06-29
forum: General Help
---

### Post by bobbob1016 on 2011-06-29
I was having issues with my raid5mdadm, either dropping a drive or getting really slow reads.  I replaced the sata card that 2 drives were connected to, and it was working fine.  I left it last night rebuilding, and woke up this morning and it failed.  It is currently saying I have 2 drives as spare and 4 as raid, but won't go anywhere further.  I've read I can basically do a create again, but I'd like some reassurances that I won't lose my data by doing that.  Here is a mdadm --examine of the drives in question, followed by an --assemble --scan --verbose.  I would appreciate any advice/help.

sudo mdadm --examine /dev/sd[bcdefg]1
/dev/sdb1:
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

    Update Time : Wed Jun 29 07:47:10 2011
          State : clean
 Active Devices : 4
Working Devices : 6
 Failed Devices : 2
  Spare Devices : 2
       Checksum : 32dfc95c - correct
         Events : 86546

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       17        2      active sync   /dev/sdb1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       97        3      active sync   /dev/sdg1
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
   6     6       8       81        6      spare   /dev/sdf1
   7     7       8       65        7      spare   /dev/sde1
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

    Update Time : Wed Jun 29 07:47:10 2011
          State : clean
 Active Devices : 4
Working Devices : 6
 Failed Devices : 2
  Spare Devices : 2
       Checksum : 32dfc96a - correct
         Events : 86546

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       97        3      active sync   /dev/sdg1
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
   6     6       8       81        6      spare   /dev/sdf1
   7     7       8       65        7      spare   /dev/sde1
/dev/sdd1:
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

    Update Time : Wed Jun 29 07:47:10 2011
          State : clean
 Active Devices : 4
Working Devices : 6
 Failed Devices : 2
  Spare Devices : 2
       Checksum : 32dfc978 - correct
         Events : 86546

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       49        0      active sync   /dev/sdd1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       97        3      active sync   /dev/sdg1
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
   6     6       8       81        6      spare   /dev/sdf1
   7     7       8       65        7      spare   /dev/sde1
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

    Update Time : Wed Jun 29 07:47:10 2011
          State : clean
 Active Devices : 4
Working Devices : 6
 Failed Devices : 2
  Spare Devices : 2
       Checksum : 32dfc990 - correct
         Events : 86546

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     7       8       65        7      spare   /dev/sde1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       97        3      active sync   /dev/sdg1
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
   6     6       8       81        6      spare   /dev/sdf1
   7     7       8       65        7      spare   /dev/sde1
/dev/sdf1:
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

    Update Time : Wed Jun 29 07:47:10 2011
          State : clean
 Active Devices : 4
Working Devices : 6
 Failed Devices : 2
  Spare Devices : 2
       Checksum : 32dfc99e - correct
         Events : 86546

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8       81        6      spare   /dev/sdf1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       97        3      active sync   /dev/sdg1
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
   6     6       8       81        6      spare   /dev/sdf1
   7     7       8       65        7      spare   /dev/sde1
/dev/sdg1:
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

    Update Time : Wed Jun 29 07:47:10 2011
          State : clean
 Active Devices : 4
Working Devices : 6
 Failed Devices : 2
  Spare Devices : 2
       Checksum : 32dfc9ae - correct
         Events : 86546

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       97        3      active sync   /dev/sdg1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       97        3      active sync   /dev/sdg1
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
   6     6       8       81        6      spare   /dev/sdf1
   7     7       8       65        7      spare   /dev/sde1

sudo mdadm --assemble --scan --verbose
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 7.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 6.
mdadm: /dev/sdg1 is identified as a member of /dev/md0, slot 3.
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: added /dev/sdb1 to /dev/md0 as 2
mdadm: added /dev/sdg1 to /dev/md0 as 3
mdadm: no uptodate device for slot 4 of /dev/md0
mdadm: no uptodate device for slot 5 of /dev/md0
mdadm: added /dev/sdf1 to /dev/md0 as 6
mdadm: added /dev/sde1 to /dev/md0 as 7
mdadm: added /dev/sdd1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 4 drives and 2 spares - not enough to start the array.

---

