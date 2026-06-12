---
title: "mdadm RAID5 issue"
date: 2012-02-08
forum: General Help
---

### Post by Snowjoggs on 2012-02-08
so my RAID5 have been humming along nicely since my last incident a year ago which I resolved in this thread [http://ubuntuforums.org/showthread.php?t=1689828&page=3](http://ubuntuforums.org/showthread.php?t=1689828&page=3)

Now it failed again, I did a cat /prod/mdstat and two of my drives had gone inactive and the raid was in read-only mode. Ok... Ill just reboot and try my luck I thought

Now this greets me

```
klingon@enterprise:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdh1[5](S) sdf1[6](S) sdg1[4](S) sde1[3](S) sdd1[2](S) sdc1[1](S) sdb1[0](S)
      6837319552 blocks

unused devices: <none>

```I try my own fix from my old thread, but to no avail

```
root@enterprise:~# mdadm --stop /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: stopped /dev/md0

root@enterprise:~# mdadm --assemble --scan --force /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: no devices found for /dev/md0

```Here's info from mdadm -E /dev/sd[bcdefgh]1

```
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 7
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Feb  7 21:34:27 2012
          State : active
 Active Devices : 6
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 0
       Checksum : c7e10219 - correct
         Events : 1249638

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       81        6      active sync   /dev/sdf1

/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 7
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Feb  7 21:34:59 2012
          State : active
 Active Devices : 5
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 0
       Checksum : c7e1025e - correct
         Events : 1249640

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       81        6      active sync   /dev/sdf1

/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 7
  Total Devices : 7
Preferred Minor : 0

    Update Time : Mon Jan 16 20:51:31 2012
          State : active
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c7addcca - correct
         Events : 1050673

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       81        6      active sync   /dev/sdf1

/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 7
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Feb  7 21:34:59 2012
          State : active
 Active Devices : 5
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 0
       Checksum : c7e10282 - correct
         Events : 1249640

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       65        3      active sync   /dev/sde1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       81        6      active sync   /dev/sdf1

/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 7
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Feb  7 21:34:59 2012
          State : active
 Active Devices : 5
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 0
       Checksum : c7e10298 - correct
         Events : 1249640

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8       81        6      active sync   /dev/sdf1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       81        6      active sync   /dev/sdf1

/dev/sdg1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 7
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Feb  7 21:34:59 2012
          State : active
 Active Devices : 5
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 0
       Checksum : c7e102a4 - correct
         Events : 1249640

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       97        4      active sync   /dev/sdg1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       81        6      active sync   /dev/sdf1

/dev/sdh1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1ea42a9a:8a44e4c2:163c2a05:89fa2e07
  Creation Time : Tue Jun  1 22:34:37 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
   Raid Devices : 7
  Total Devices : 6
Preferred Minor : 0

    Update Time : Tue Feb  7 21:34:59 2012
          State : active
 Active Devices : 5
Working Devices : 5
 Failed Devices : 1
  Spare Devices : 0
       Checksum : c7e102b6 - correct
         Events : 1249640

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8      113        5      active sync   /dev/sdh1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      113        5      active sync   /dev/sdh1
   6     6       8       81        6      active sync   /dev/sdf1


```

Any advice as to what I should try next?

---

### Post by Snowjoggs on 2012-02-08
So... Im kind of impatient, toying around I think I fixed it!

```
root@enterprise:/etc/mdadm# mdadm --assemble /dev/md0 /dev/sd{b,c,d,e,f,g,h}1 --force
mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 has been started with 6 drives (out of 7).
root@enterprise:/etc/mdadm# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd1[7] sdb1[0] sdf1[6] sdh1[5] sdg1[4] sde1[3] sdc1[1]
      5860559616 blocks level 5, 64k chunk, algorithm 2 [7/6] [UU_UUUU]
      [>....................]  recovery =  0.0% (387840/976759936) finish=461.5min speed=35258K/sec

```

I bet I can add the last drive once it's finished syncing. I do not think its broken, any way I could check that it is other than a normal fsck?

---

