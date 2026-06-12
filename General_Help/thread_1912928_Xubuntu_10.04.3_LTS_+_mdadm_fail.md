---
title: "Xubuntu 10.04.3 LTS + mdadm fail"
date: 2012-01-21
forum: General Help
---

### Post by Enira on 2012-01-21
So I am getting some errors with mdamd. 

I've built a RAID5 of 5 devices which seems to be offline at the moment. Physically the drives can be accessed and none seems to be broken, all lights are burning.

```
mdadm --assemble --force /dev/md0
mdadm: metadata format 00.91 unknown, ignored.
mdadm: no devices found for /dev/md0

```And when I try to assemble the raid manually it says to me:

```
mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1
mdadm: metadata format 00.91 unknown, ignored.
mdadm: /dev/md0 assembled from 3 drives - not enough to start the array.

```Additional info:
```
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e33ba676:eff30831:c7780c0e:bc15422d (local to host nas)
  Creation Time : Tue Jun  8 13:46:59 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Dec 29 15:55:07 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : d52d81b0 - correct
         Events : 77096

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       81        2      active sync   /dev/sdf1
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed



/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e33ba676:eff30831:c7780c0e:bc15422d (local to host nas)
  Creation Time : Tue Jun  8 13:46:59 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Dec 29 15:50:44 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d52d80ab - correct
         Events : 77092

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       81        2      active sync   /dev/sdf1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       33        4      active sync   /dev/sdc1


/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e33ba676:eff30831:c7780c0e:bc15422d (local to host nas)
  Creation Time : Tue Jun  8 13:46:59 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Dec 29 15:50:44 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d52d809d - correct
         Events : 77092

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       33        4      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       81        2      active sync   /dev/sdf1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       33        4      active sync   /dev/sdc1



/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e33ba676:eff30831:c7780c0e:bc15422d (local to host nas)
  Creation Time : Tue Jun  8 13:46:59 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Dec 29 15:55:07 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : d52d81f4 - correct
         Events : 77096

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       81        2      active sync   /dev/sdf1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       81        2      active sync   /dev/sdf1
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed


/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e33ba676:eff30831:c7780c0e:bc15422d (local to host nas)
  Creation Time : Tue Jun  8 13:46:59 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Thu Dec 29 15:55:07 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 0
       Checksum : d52d81e2 - correct
         Events : 77096

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       65        1      active sync   /dev/sde1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       81        2      active sync   /dev/sdf1
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed

```My guess is that sdc and sdd got disconnected at the same time, around 15:50. And the other 3 drives just kept going on till 15:55. The three drives registered the drop and are now trying to start without the two other.

Anyone any idea how I can repair this? Thanks in advance.

I've read something about this here: [https://raid.wiki.kernel.org/articles/r/e/c/Reconstruction.html](https://raid.wiki.kernel.org/articles/r/e/c/Reconstruction.html) a) Is this the solution for me? And does anyone has any info on what to do with the raidtab?

EDIT:

mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 did the trick.

---

