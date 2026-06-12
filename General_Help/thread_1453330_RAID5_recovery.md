---
title: "RAID5 recovery"
date: 2010-04-13
forum: General Help
---

### Post by shishkaberry on 2010-04-13
I'm having trouble restarting my RAID array and was wondering if anyone would be willing to lend a hand?

4 devices [sdb, sdc, sdd, sde]
 - sdc failed
 - reindexing occurred but with some strange side effects

I am unable to fully provide steps taken to get this far. So i'll just show what i can:

```

sudo mdadm --query --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Sun Jan  4 15:09:54 2009
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jan 16 23:32:15 2010
          State : active, degraded, Not Started
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : a314a551:22a6b549:12205e66:ba460938 (local to host attackalope)
         Events : 0.3711710

    Number   Major   Minor   RaidDevice State
       0       8       49        0      spare rebuilding   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1
       2       8       17        2      active sync   /dev/sdb1
       3       0        0        3      removed

```
so i try:
```

sudo mdadm --run /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: failed to run array /dev/md0: Input/output error

```

There is some inconsistency when i --examine each remaining drives:

```

sudo mdadm --examine /dev/sdb1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a314a551:22a6b549:12205e66:ba460938 (local to host attackalope)
  Creation Time : Sun Jan  4 15:09:54 2009
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Jan 16 23:32:15 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : aab83c7 - correct
         Events : 3711710

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       17        2      active sync   /dev/sdb1

   0     0       0        0        0      removed
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       0        0        3      faulty removed


```
```

sudo mdadm --examine /dev/sdd1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a314a551:22a6b549:12205e66:ba460938 (local to host attackalope)
  Creation Time : Sun Jan  4 15:09:54 2009
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Jan 16 23:31:12 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : aab8391 - correct
         Events : 3711706

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       49        0      active sync   /dev/sdd1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       0        0        3      faulty removed


```
```

sudo mdadm --examine /dev/sde1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a314a551:22a6b549:12205e66:ba460938 (local to host attackalope)
  Creation Time : Sun Jan  4 15:09:54 2009
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Jan 16 23:32:15 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : aab83f5 - correct
         Events : 3711710

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       65        1      active sync   /dev/sde1

   0     0       0        0        0      removed
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       0        0        3      faulty removed

```

so what now?

---

