---
title: "Raid 5 problem after wakeup from powersave"
date: 2009-08-30
forum: General Help
---

### Post by skylizard on 2009-08-30
Hey guys,
I got aproblem here with my Raid 5.
I'm running ubuntu 9.04 and got a Raid 5 with 4 HDD's built with mdadm.
After wakeup from powersave there were 3 out of 4 drives removed from the raid.
Another reboot didn't solve the problem.
It now looks like this:

```
lizardking@linuxtier:~$ sudo mdadm --detail /dev/md1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
/dev/md1:
        Version : 00.90
  Creation Time : Tue Apr 28 14:04:18 2009
     Raid Level : raid1
     Array Size : 8787456 (8.38 GiB 9.00 GB)
  Used Dev Size : 8787456 (8.38 GiB 9.00 GB)
   Raid Devices : 4
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Aug 30 15:26:08 2009
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : bc08bfde:b1b50536:60a89728:54d85aae
         Events : 0.4047

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       0        0        2      removed
       3       8       53        3      active sync   /dev/sdd5

```What can I do to get this raid running again.

Will a simple re-add with

mdadm /dev/md2 -a /dev/sda5

work when done with all devices?
Thanks in advance,
skylizard

---

