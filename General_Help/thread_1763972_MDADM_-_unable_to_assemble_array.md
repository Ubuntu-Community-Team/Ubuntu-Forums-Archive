---
title: "MDADM - unable to assemble array"
date: 2011-05-21
forum: General Help
---

### Post by Onthax on 2011-05-21
Hi guys

trying to troubleshoot an issue i'm having with MDADM

I have a raid 5 array consisting of 5 2tb Western Digital Green drives.

It has been working fine for the last 6-7 months but recently has stopped working.

After rebooting i get an error something like "unable to mount /mnt/storage" which is the filesystem on the raid array

the raid array is /dev/md0
when i do a " sudo mdadm --assemble --scan"
i get the error mdadm: /dev/md0 assembled from 3 drives - not enough to start the array

all the drives are there and i can see the correct partition information if i load them up in parted.

Not sure what's going on here, anyone have any insight?

---

### Post by Onthax on 2011-05-21
when i do 
sudo mdadm --examine /dev/sdb1

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       0        0        4      faulty removed


however the drives are still there and i know they are clean

and if i do 
sudo mdadm --examine /dev/sdc1 i get this

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1

---

