---
title: "Raid 1 - no superblock - help"
date: 2009-10-30
forum: General Help
---

### Post by apollard on 2009-10-30
I have a desktop running a raid 1 array. Today, a connector died, and I lost power to both raid drives. I get a fsk error saying no /bad superblock on /dev/md0 during boot. I tired to assemble the md, to no avail. Here's the log:

fsck.ext3: Invalid argument while trying to open /dev/md0

/dev/md0: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Trying e2fsk as above gave me a command not found error.
So, I did some research, and here's what mdadm tells me:
mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.

mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 6583fba1:0eb56504:d47be3dc:4b3835ad (local to host hnserver)
  Creation Time : Sun Aug 17 18:23:25 2008
     Raid Level : raid1
  Used Dev Size : 117185984 (111.76 GiB 120.00 GB)
     Array Size : 117185984 (111.76 GiB 120.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Fri Oct 30 20:58:13 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d7aaae4f - correct
         Events : 0.51950


      Number   Major   Minor   RaidDevice State
this     1       8       49        1      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       49        1      active sync   /dev/sdd1
mdadm --examine /dev/sdb1
mdadm: No md superblock detected on /dev/sdb1.

All disks are recognized by bios, gparted, and fdisk. TestDisk shows nothing missing, but of course, /dev/sdb1 with a bad superblock. After reading some in the forums, I tried this:
 mdadm --create --assume-clean /dev/md0 /dev/sdd1 missing
mdadm: no raid-disks specified.


How can I salvage the data or reactivate the array? I have a backup, but of course, it's a month old.

---

