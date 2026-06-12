---
title: "Can't convert RAID6 to RAID5"
date: 2012-05-17
forum: General Help
---

### Post by Lazy Ranma on 2012-05-17
I have 5 1TB HDDs in RAID6, and I want to convert this array to RAID5. I converted block layout to transitional left-symmetric-6 beforehand, now all mdadm needs to do is to discard the last drive and change level to 5.
The problem is, when I try to change raid level, nothing happens. Well, mdadm 3.2.3 shipped with Ubuntu 12.04 just crashes, but I'm using 3.2.4-1 from Debian and tried latest version from git.

```
$ uname -a
Linux ### 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
$ cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] [raid1] [linear] [multipath] [raid0] [raid10] 
md1 : active raid1 sdc2[8] sda2[6] sdb2[2] sdd2[7] sde2[5]
      203764 blocks super 1.0 [5/5] [UUUUU]
      bitmap: 0/7 pages [0KB], 16KB chunk

md0 : active raid6 sdc1[8] sda1[6] sdb1[4] sdd1[7] sde1[5]
      2929672896 blocks super 1.2 level 6, 32k chunk, algorithm 18 [5/5] [UUUUU]
      
unused devices: <none>
$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon May 25 01:51:42 2009
     Raid Level : raid6
     Array Size : 2929672896 (2793.95 GiB 2999.99 GB)
  Used Dev Size : 976557632 (931.32 GiB 1000.00 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Thu May 17 21:38:28 2012
          State : clean 
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric-6
     Chunk Size : 32K

           Name : lagann:0
           UUID : f86374bb:902f2363:5b3f244a:2b68371c
         Events : 11148881

    Number   Major   Minor   RaidDevice State
       5       8       65        0      active sync   /dev/sde1
       4       8       17        1      active sync   /dev/sdb1
       8       8       33        2      active sync   /dev/sdc1
       6       8        1        3      active sync   /dev/sda1
       7       8       49        4      active sync   /dev/sdd1


$ mdadm --version
mdadm - v3.2.4 - 9th May 2012
$sudo /gurren/home/ranma/src/mdadm/mdadm --grow /dev/md0 --level=raid5
raid_disks for /dev/md0 set to 4

```(after that nothing happens, nothing is written to syslog)

Any ideas why nothing happens, or how to convert the array?

---

### Post by Lazy Ranma on 2012-05-17
I should have tried older version before posting...
With mdadm 3.1.5 everything worked like a charm. I hope this post helps if someone encounter a similar problem.

---

