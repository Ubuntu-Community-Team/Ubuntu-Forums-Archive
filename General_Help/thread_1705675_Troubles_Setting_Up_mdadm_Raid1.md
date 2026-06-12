---
title: "Troubles Setting Up mdadm Raid1"
date: 2011-03-12
forum: General Help
---

### Post by wittrura on 2011-03-12
Greetings,

I recently updated my computer with a SYBA SATA controller card and two Samsung 2TB HDD to use as a backend for all my media.  I wanted to use the harddrives in RAID1 as I've had an external die in the past that caused quite a lot of problems.

I've read through the forums and Ubuntu user guide and have been have some frustrating results using mdadm to set up the software raid.  I initially had everything working fine - I formatted both drives, then used mdadm to create /dev/md0, and was transferring files with Samba and no problems.

Upon a restart, the /dev/md0 was no longer mounted, and using fdisk I discovered the name was now /dev/md_0, and when I mounted all information was gone.

I started over, stopped that array, created a new one using my harddrives, and again everything was working fine.  Then a restart and problems again.

Drive was unmounted, and when I used --assemble, I am receiving the error You are not privileged to mount the volume "2T Volume"

Below are some outputs:
:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat Mar 12 08:21:52 2011
     Raid Level : raid1
     Array Size : 1953514496 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Mar 12 15:23:08 2011
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 70c6e86c:2067da50:8e7e0cb4:752f0ea8
         Events : 0.26


    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       0        0        1      removed



:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c14a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19267   154754048   83  Linux
/dev/sda2           19267       19458     1533953    5  Extended
/dev/sda5           19267       19458     1533952   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/md0: 2000.4 GB, 2000398843904 bytes
2 heads, 4 sectors/track, 488378624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


I should also add that if I do mount /dev/md0, I am seeing the files I transferred before the restart.

My main concern now is 1) why is the 2nd harddrive not being assembled? and 2) why is nothing saved from a restart?

Thanks in advance for any help you may be able to offer.  I have been away from Ubuntu for a little while now, but this forum was incredible when I was learning Gutsy so I'm hoping all the bright members are still here :KS

---

