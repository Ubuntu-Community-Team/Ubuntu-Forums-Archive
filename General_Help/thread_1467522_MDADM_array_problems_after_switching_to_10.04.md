---
title: "MDADM array problems after switching to 10.04"
date: 2010-04-30
forum: General Help
---

### Post by nairb11 on 2010-04-30
I was running 8.11 and had a working raid5 array (6 disks) using mdadm.  I took out the os drive and install 10.04 on a new drive.  After installing mdadm on the new os I tried 

mdadm --assemble --scan

and it assembled /dev/md0 with 5 out of 6 drives, stating the last drive was removed.  I tried to add it back and it said the device was busy.  I put the 8.11 drive back in and the array came back with 5/6 drives and I was able to rebuild to a clean, non degraded array.

I switched back to the 10.04 drive and tried to assemble again specifying the drives:

mdadm --assemble /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1

and got:

mdadm: cannot open device /dev/sdb1: Device or resource busy 
mdadm: /dev/sdb1 has no superblock - assembly aborted

then tried:

mdadm --assemble -f /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1
mdadm: no recogniseable superblock on /dev/sda1
mdadm: /dev/sda1 has no superblock - assembly aborted

still no luck.  I put the 8.11 drive back in and rebuilt the array again.

Any ideas what I'm doing wrong when trying to reassemble the array under 10.04? 

the clean array under 8.11 looks like this:

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       6       8       17        3      active sync   /dev/sdb1
       4       8       97        4      active sync   /dev/sdg1
       5       8       81        5      active sync   /dev/sdf1

---

### Post by nairb11 on 2010-05-01
a little more info...

When I do mdadm -E on each drive all have the same UUID and version info except /dev/sda1 which says:

mdadm: No md superblock detected on /dev/sda1.

I imagine this is causing the problem when trying to assemble the array in my new system?

---

### Post by rabban on 2010-05-27
Hi

I'm having similar problems with Raid5 after upgrading from 9.01 to 10.04. Only difference is that I had a 7 disk raid where one disk was flaky. After upgrade to 10.04 I now have a a failed disk and a flaky one that only sometimes adds to the raid...

Have you found a solution to your problem?

---

### Post by nairb11 on 2010-05-27
Yes.  First I put in my original harddrive with 8.11 still installed and rebuilt the bad drive so I had a non degraded array.  Then put my 10.04 drive back in and added the following line to mdadm.conf and rebooted:

ARRAY /dev/md0 level=raid5 num-devices=6 metadata=0.90 UUID=48c840d0:ef028c1b:500c5acc:68ce6167

It mounted just fine after that, been running for about 3 weeks now with no issues.

---

