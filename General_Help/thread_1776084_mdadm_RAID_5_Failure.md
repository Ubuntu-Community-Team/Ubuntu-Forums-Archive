---
title: "mdadm RAID 5 Failure"
date: 2011-06-05
forum: General Help
---

### Post by inxfernxo on 2011-06-05
After a power outage I lost 1/4 drives and the spare supposedly kicked in but never rebuilt.


-------
sudo mdadm --assemble --run --force /dev/md0 /dev/sdd1 /dev/sdf1 /dev/sdg1

mdadm: Unknown keyword âDEVICE
mdadm: cannot open device /dev/sdf1: Device or resource busy
mdadm: **[COLOR=Red]/dev/sdf1 has no superblock - assembly aborted[/COLOR]**
---------


I rebooted the server and ran --detail


-----------
    Update Time : Sat Jun  4 18:56:53 2011
          State : [COLOR=Red]**active, degraded, Not Started**[/COLOR]
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : :Data_Drives_01
           UUID : bb2b61b9:2a562ab2:81e4a7a6:c5e8439b
         Events : 2493057

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       49        1      active sync   /dev/sdd1
       3       8       97        2      **[COLOR=Red]spare rebuilding   /dev/sdg1[/COLOR]**
----------------

It's been "Rebuilding" for 2 days now.... I don't think it really is actually doing anything though.

---

### Post by inxfernxo on 2011-06-05
Rebooted and tried again.


demigod@BAS01:~$ sudo mdadm --examine /dev/md0
[COLOR=Red]**mdadm: No md superblock detected on /dev/md0.**[/COLOR]


sudo mdadm --assemble --run --force /dev/md0 /dev/sdd1 /dev/sdf1 /dev/sdg1
[COLOR=Red][B]mdadm:/ Input/output error
mdadm: /dev/sdg1 has no superblock - assembly aborted[/B][/COLOR]

---

