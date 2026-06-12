---
title: "mdadm gurus, please help me"
date: 2010-04-10
forum: General Help
---

### Post by pablo79 on 2010-04-10
Dear all,
 I've created a RAID 5 with 3 disks but now the system is not able to start it.

This is the situation:
```

sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : bdb6ebf8:a3117b71:c5d110f2:f9137e1d (local to host mythtv)
  Creation Time : Thu Apr  8 01:54:10 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0

    Update Time : Fri Apr  9 21:11:07 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : d4c629b1 - correct
         Events : 2354

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed

```

```
sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : bdb6ebf8:a3117b71:c5d110f2:f9137e1d (local to host mythtv)
  Creation Time : Thu Apr  8 01:54:10 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0

    Update Time : Fri Apr  9 21:11:07 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : d4c629c3 - correct
         Events : 2354

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed

```
```
sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : bdb6ebf8:a3117b71:c5d110f2:f9137e1d (local to host mythtv)
  Creation Time : Thu Apr  8 01:54:10 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Apr  9 08:04:07 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d4c55f71 - correct
         Events : 30

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1

```
```
sudo mdadm -v --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has no superblock - assembly aborted

```
```
sudo mdadm -A --scan -v
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: /dev/sde1 has wrong uuid.
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sde has wrong uuid.
mdadm: /dev/sdd1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdd has wrong uuid.
mdadm: /dev/sdc1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.
mdadm: no devices found for /dev/md0
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sdd1 is identified as a member of /dev/md/0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md/0, slot 1.
mdadm: no uptodate device for slot 0 of /dev/md/0
mdadm: added /dev/sdd1 to /dev/md/0 as 2
mdadm: added /dev/sdc1 to /dev/md/0 as 1
mdadm: /dev/md/0 assembled from 1 drive - not enough to start the array.
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/sdd
mdadm: no recogniseable superblock on /dev/sdc

```
Is it possible to recover my raid?

Thank you all

---

### Post by pablo79 on 2010-04-10
Nothing to try? Do I have say hello to my data? :(

---

