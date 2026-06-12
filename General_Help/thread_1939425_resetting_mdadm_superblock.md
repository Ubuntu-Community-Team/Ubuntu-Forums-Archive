---
title: "resetting mdadm superblock"
date: 2012-03-11
forum: General Help
---

### Post by Cr0n_J0b on 2012-03-11
Hey folks,

I'm having some issues with my md array after upgrading to 11.04.

In my case I have an RAID0 array created from 2 devices (See below)

Boot drives:  /dev/sda1
raid 0 dev 1: /dev/sdb1
raid 0 dev 2: /dev/sdc1

RAID device is: /dev/md0

The issue is that the super blocks for /dev/sdb1 and /dev/sdc1 look like this.

----------------
root@uNAS:~# mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 3424db31:eeb216cb:4c0d2395:9c0bfdf6 (local to host uNAS)
  Creation Time : Mon Nov  9 20:31:42 2009
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Feb 13 11:03:20 2011
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4c6d7ae7 - correct
         Events : 13

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
---------------
root@uNAS:~# mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 3424db31:eeb216cb:4c0d2395:9c0bfdf6 (local to host uNAS)
  Creation Time : Mon Nov  9 20:31:42 2009
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Feb 13 11:03:20 2011
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4c6d7af9 - correct
         Events : 13

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
--------

the array will start with:
mdadm -A --update=super-minor /dev/md0 /dev/sdb1 /dev/sdc1

and the array looks like this:
root@uNAS:~# mdadm -Q --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Mon Nov  9 20:31:42 2009
     Raid Level : raid0
     Array Size : 3904887168 (3723.99 GiB 3998.60 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Feb 13 11:03:20 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 3424db31:eeb216cb:4c0d2395:9c0bfdf6 (local to host uNAS)
         Events : 0.13

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
--------------

but for some reason the super block isn't being updated...so the array won't autostart.  My understanding is that the update=super-minor tells the system to start each drive and update the minor field...which I thought would fix this.

here is the ooutput from the start up:

---------------
root@uNAS:~# mdadm -Av --update=super-minor /dev/md0 /dev/sdb1 /dev/sdc1
mdadm: looking for devices for /dev/md0
mdadm: updating superblock of /dev/sdb1 with minor number 0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 0.
mdadm: updating superblock of /dev/sdc1 with minor number 0
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: added /dev/sdb1 to /dev/md0 as 0
mdadm: /dev/md0 has been started with 2 drives.

-------------------

Anyone know what's going on?

thanks.

---

### Post by Cr0n_J0b on 2012-03-12
does anyone have insight? should I post to a different group?

---

### Post by Cr0n_J0b on 2012-03-16
Can anyone help with this?

---

