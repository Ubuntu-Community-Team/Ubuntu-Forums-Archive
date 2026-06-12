---
title: "md0: unknown partition table"
date: 2009-10-29
forum: General Help
---

### Post by eppo on 2009-10-29
when i try to start my raid 5 raid array, i get:
 md0: unknown partition table 
in dmesg. is there anyway to alter the partition table info without losing the info i have on the array?

---

### Post by Giblet5 on 2009-10-29
> **eppo said:**
> when i try to start my raid 5 raid array, i get:
 md0: unknown partition table 
in dmesg. is there anyway to alter the partition table info without losing the info i have on the array?

Not really, and that isn't likely your problem. Writing to it in any way at this point will not end well, unless there's nothing on it.

The array, if it's a software raid implementation, probably isn't being assembled in the correct order.

Is this a software raid array?

Is this a brand new SAN array?

---

### Post by phillw on 2009-10-29
> **eppo said:**
> when i try to start my raid 5 raid array, i get:
 md0: unknown partition table 
in dmesg. is there anyway to alter the partition table info without losing the info i have on the array?

there's some good stuff here ... [http://www.dedoimedo.com/computers/linux-raid.html](http://www.dedoimedo.com/computers/linux-raid.html)

Hopefully it'll point you in the right direction.

Regards,

Phill.

---

### Post by eppo on 2009-10-29
this is a software raid created with mdadm:
/dev/md0:
        Version : 00.90
  Creation Time : Sun Sep  7 14:39:47 2008
     Raid Level : raid5
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Oct 29 12:31:20 2009
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 69a2ea09:b978d90b:9c682ae7:cd63b594
         Events : 0.917968

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8        1        1      active sync   /dev/sda1
       2       8       17        2      active sync   /dev/sdb1
       3       8       65        3      active sync   /dev/sde1
       4       8       49        4      active sync   /dev/sdd1

---

### Post by Giblet5 on 2009-10-29
Did you reinstall or upgrade the OS?

Software raid is the affordable short-path to data loss.

In the future, you'll be happier with a hardware RAID controller. I like Adaptec's SATA raid controller for PCI-e.

---

### Post by eppo on 2009-10-29
yup, 8.10 to 9.04

---

### Post by Giblet5 on 2009-10-29
Did you save your mdadm.conf file from Intrepid?

Did you do a backup?

---

### Post by eppo on 2009-10-29
no i do believe i just took the new version. 
i didnt back up. i figured if the hardware was working fine it would after the upgrade.  
is there a way to change the order of the drives?

---

### Post by eppo on 2009-10-29
can i rebuild the raid without losing data?
read something about using mdadm --build?

---

### Post by eppo on 2009-11-02
i found that the superblock info that i need is on /dev/sde1.
is there anyway to recreate the array with /dev/sde1 being the first disk? or be able to tell it when it mounts that the superblock info is there?

---

### Post by _iridium_ on 2010-05-20
Same f*$·%& issue upgrading from 8.04 to 10.04.

Also having a "soft" raid0....not a hardware controller.

Any possible solution?

---

### Post by derek71 on 2010-07-01
I am running into a similar problem, I am building a NAS with Ubuntu 10.04 server.

When I check syslog for messages related to the RAID, I see "md0: unknown partition table".

I should add that mdadm indicates that the array is clean, though fdisk -l reports that the raid partition doesn't contain a valid partition table.

After reading some other posts, I noticed that the order of the raid devices does not match the order specified in the configuration.

---

### Post by runesvend on 2010-07-09
> **derek71 said:**
> When I check syslog for messages related to the RAID, I see "md0: unknown partition table".

I should add that mdadm indicates that the array is clean, though **fdisk -l reports that the raid partition doesn't contain a valid partition table.**
Couldn't this be the issue? That the device does not contain a valid partition table?

I just ran into this problem as well, and found this thread. Then I realized than I had forgotten to partition my raid device (/dev/md1) before putting an ext4 file system on it. I guess this is the reason for the error/warning. It just seemed unnecessary to partition a RAID-device that consists of two partitions. That'd be like partitioning a partition...

But the RAID partition mounts fine for me, so it seems to only be a warning. Does it not mount correctly for you?

***EDIT:** Could someone enlighten us (or at least the ones of us for whom the RAID-device mounts correctly) on whether this could be a problem. Ie. should we, if possible, move the data on the RAID-device to a safe location, create a partition on the RAID-device, create a file system on that partition, and copy the data back? Is there any reason to do this (besides getting rid of that warning)?*

---

### Post by runesvend on 2010-07-10
This warning shouldn't be an issue if all else works for you: [http://marc.info/?l=linux-raid&m=125797242110594&w=2](http://marc.info/?l=linux-raid&m=125797242110594&w=2)

---

### Post by derek71 on 2010-07-11
When I first built my RAID via mdadm, I did not see anything in the various howtos about partitioning the RAID, just the individual drives.

If this message is just a remnant of an earlier version of the OS, then I may be all set to go.

Aside from fdisk and mdadm, what other tools/tests should I apply to check RAID integrity?

---

