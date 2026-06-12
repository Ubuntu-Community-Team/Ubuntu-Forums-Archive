---
title: "mdadm lost RAID 5 volume: device or resource busy"
date: 2011-01-14
forum: General Help
---

### Post by ericnyc on 2011-01-14
Hello everyone.

My first time getting to this point where I can't fix something myself.  Looking for any input to this vexing problem of mine that has taken many hours of my life.

I have a new 4-bay eSATA enclosure plugged into some POS fakeraid card. Ubuntu 10.10 can see all 4 drives but I am unable to online the RAID set after it somehow stopped working.

When the RAID array went down, the initial building of the last drive was still going on.

I have tried booting with the kernel option "nodmraid". I have ensured that I don't have dmraid installed. I have confirmed lsof shows nothing.

Details:

root@media2:~# mdadm --verbose --assemble --update=resync /dev/md1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: looking for devices for /dev/md1
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdc1 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdd1 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sde1 is identified as a member of /dev/md1, slot 4.
mdadm: Cannot open /dev/sdb1: Device or resource busy
root@media2:~# 


root@media2:~# fdisk -l

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x278aa9cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x355886ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1a1103b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x403fd1f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001   fd  Linux raid autodetect






root@media2:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sde1[4](S) sdd1[2](S) sdc1[1](S) sdb1[0](S)
      7814047744 blocks
       
unused devices: <none>
root@media2:~# 










root@media2:~# mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 90a6ec96:41c82680:86f2464e:5fa4ba3e (local to host media2)
  Creation Time : Wed Jan 12 19:07:35 2011
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Thu Jan 13 21:26:14 2011
          State : active
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 7101323d - correct
         Events : 20147

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       0        0        3      faulty removed
   4     4       8       65        4      spare   /dev/sde1
root@media2:~# mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 90a6ec96:41c82680:86f2464e:5fa4ba3e (local to host media2)
  Creation Time : Wed Jan 12 19:07:35 2011
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Thu Jan 13 23:55:10 2011
          State : active
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 7101551c - correct
         Events : 20154

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       65        4      spare   /dev/sde1
root@media2:~# mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 90a6ec96:41c82680:86f2464e:5fa4ba3e (local to host media2)
  Creation Time : Wed Jan 12 19:07:35 2011
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Thu Jan 13 23:55:10 2011
          State : active
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 7101552e - correct
         Events : 20154

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       65        4      spare   /dev/sde1
root@media2:~# mdadm --examine /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 90a6ec96:41c82680:86f2464e:5fa4ba3e (local to host media2)
  Creation Time : Wed Jan 12 19:07:35 2011
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Thu Jan 13 23:55:10 2011
          State : active
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 7101554e - correct
         Events : 20154

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       65        4      spare   /dev/sde1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       65        4      spare   /dev/sde1
root@media2:~#

---

### Post by ericnyc on 2011-01-14
bump!

---

### Post by ericnyc on 2011-01-15
Can someone help me?

---

