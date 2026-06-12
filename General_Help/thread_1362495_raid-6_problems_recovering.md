---
title: "raid-6 problems recovering"
date: 2009-12-23
forum: General Help
---

### Post by QrK0 on 2009-12-23
Last day, the sata controller made something wrong (maybe was a disk time-out), and it stoped my raid-6.
This raid-6 was composed by 12 disks, 1TB each one.
```
# cat /proc/mdstat
Personalities : [raid1] [raid0] [raid6] [raid5] [raid4] 
md2 : inactive sdb1[1](S) sdl1[11](S) sdk1[10](S) sdj1[9](S) sdi1[8](S) sdh1[7](S) sdg1[6](S) sdf1[5](S) sde1[4](S) sdd1[3](S) sdc1[2](S) sda1[0](S)
      11721119232 blocks

```
So all devices are now marked as spare.

mdadm -E shows the same UUID in all devices. The only difference between each device is the events and the state: 3 of 12 disks shows events:28 and state clean. The rest of disks shows events:15 and state active.

For /dev/sd{a,c,d,e,f,g,i,k,l}1
```
# mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : f9b5de44:ae13c50b:75a32c2e:f213c968 (local to host CIMD-B05)
  Creation Time : Mon Jul  6 15:46:48 2009
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 9767599360 (9315.11 GiB 10002.02 GB)
   Raid Devices : 12
  Total Devices : 12
Preferred Minor : 2

    Update Time : Thu Dec 17 09:52:04 2009
          State : active
 Active Devices : 12
Working Devices : 12
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 88601beb - correct
         Events : 15

     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       65        4      active sync   /dev/sde1
   5     5       8       81        5      active sync   /dev/sdf1
   6     6       8       97        6      active sync   /dev/sdg1
   7     7       8      113        7      active sync   /dev/sdh1
   8     8       8      129        8      active sync   /dev/sdi1
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       8      161       10      active sync   /dev/sdk1
  11    11       8      177       11      active sync   /dev/sdl1

```
For /dev/sd{b,h,j}1
```
# mdadm -E /dev/sdj1
/dev/sdj1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : f9b5de44:ae13c50b:75a32c2e:f213c968 (local to host CIMD-B05)
  Creation Time : Mon Jul  6 15:46:48 2009
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 9767599360 (9315.11 GiB 10002.02 GB)
   Raid Devices : 12
  Total Devices : 12
Preferred Minor : 2

    Update Time : Thu Dec 17 10:10:07 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 8
  Spare Devices : 0
       Checksum : 8860222b - correct
         Events : 28

     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     9       8      145        9      active sync   /dev/sdj1

   0     0       0        0        0      removed
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       0        0        4      faulty removed
   5     5       0        0        5      faulty removed
   6     6       0        0        6      faulty removed
   7     7       8      113        7      active sync   /dev/sdh1
   8     8       0        0        8      faulty removed
   9     9       8      145        9      active sync   /dev/sdj1
  10    10       0        0       10      faulty removed
  11    11       0        0       11      faulty removed

```

I'm almost sure that data is still there as no writes have presumably done.
Any help will be appreciated.

---

