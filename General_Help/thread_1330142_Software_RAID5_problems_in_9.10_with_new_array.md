---
title: "Software RAID5 problems in 9.10 with new array"
date: 2009-11-18
forum: General Help
---

### Post by plind69 on 2009-11-18
I've been trying over and over to setup a whole new software RAID5 array in Ubuntu 9.10 on a whole new machine, containing 3 1,5TB Western Digital SATA drives, but to no avail. I followed the tutorials out there, but things first seem to go wrong for me when I execute “mdadm –details --scan” and I get back:
> ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 spares=1 UUID=02229c0c:b3bf7f25:ead3296a:a14b1f73
Most notably, I get the “metadata” attribute and the “spares” attribute.

Running “mkfs.ext3 /dev/md0” goes fine (so it seems), but when i run “tune2fs -m 0 /dev/md0”, the first errors start happening:

> tune2fs 1.41.9 (22-Aug-2009)
tune2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/md0
Couldn't find valid filesystem superblock.
Then when I want to mount the array with “mount -a, I get the following error:
> mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing quotepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
The suggested command “dmesg | tail¨ returns:

> [40245.334901] Buffer I/O error on device md0, logical block 1
[40245.334903] Buffer I/O error on device md0, logical block 2
[40245.334906] Buffer I/O error on device md0, logical block 3
[40245.334911] Buffer I/O error on device md0, logical block 0
[40245.359610] Buffer I/O error on device md0, logical block 0
[40245.359621] Buffer I/O error on device md0, logical block 1
[40245.359625] Buffer I/O error on device md0, logical block 2
[40245.359628] Buffer I/O error on device md0, logical block 3
[40245.359631] Buffer I/O error on device md0, logical block 4
[40404.587948] EXT3-fs: unable to read superblock
Lastly, "mdadm --detail --verbose /dev/md0" returns:

> mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Tue Nov 17 23:07:58 2009
     Raid Level : raid5
     Array Size : 2930271872 (2794.53 GiB 3000.60 GB)
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Nov 18 08:24:39 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 02229c0c:b3bf7f25:ead3296a:a14b1f73
         Events : 0.14

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed

       3       8       49        -      spare   /dev/sdd1
       4       8       17        -      faulty spare   /dev/sdb1
I have tried creating this array 3 or 4 times now. Only the first time I had a bit of more luck, but after reboot things started going wrong. I have also formatted the individual disks and ran gparted disk check on them, to check if all disks were okay. No errors were reported.

Can anyone help me out? I'm stuck and very frustrated by now; especially since each creation takes 10 hours or so!

Thanks!

Pascal.

---

### Post by plind69 on 2009-11-19
Since mdadm did report one of the disks was faulty, I thought I'd dig into that with smartmontools. And what do you know? That particular disk had bad sectors, even though it was brand new! So mdadm was right after all. I returned the drive and hopefully, when the new one comes, all will work as illustrated in the several tutorials out there.

---

