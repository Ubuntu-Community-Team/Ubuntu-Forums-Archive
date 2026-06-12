---
title: "How to fix mismatch between raid size and partition sizes"
date: 2012-06-30
forum: General Help
---

### Post by Fake51 on 2012-06-30
I recently had a problem with my NAS - it has a software raid setup, with two 2TB drives. I shut the thing down, took out the drives and then checked them using gparted. Apparently that was the wrong thing to do, because gparted decided that both drives needed resizing (even though I just ran a check).

Now, the drives themselves mount just fine if I mount them individually with mount -t ext4. However, when I put them back in the NAS, the size is of course different between the drives and the RAID. So, when I try to mount the RAID I get the following in message:

[  755.560000] EXT4-fs (md0): bad geometry: block count 487986423 exceeds size of device (487986400 blocks)

fdisk outputs:

[~] # fdisk -l

Disk /dev/sda: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          66      530125   83  Linux
/dev/sda2              67         132      530142   83  Linux
/dev/sda3             133      243138  1951945693   83  Linux
/dev/sda4          243139      243200      498012   83  Linux

Disk /dev/sda4: 469 MB, 469893120 bytes
2 heads, 4 sectors/track, 114720 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/sda4 doesn't contain a valid partition table

Disk /dev/sdb: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          66      530125   83  Linux
/dev/sdb2              67         132      530142   83  Linux
/dev/sdb3             133      243138  1951945693   83  Linux
/dev/sdb4          243139      243200      498012   83  Linux

Disk /dev/md9: 542 MB, 542769152 bytes
2 heads, 4 sectors/track, 132512 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md9 doesn't contain a valid partition table

Disk /dev/md0: 1998.7 GB, 1998792294400 bytes
2 heads, 4 sectors/track, 487986400 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md2: 542 MB, 542769152 bytes
2 heads, 4 sectors/track, 132512 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md2 doesn't contain a valid partition table

mdadm details for the raid:

[~] # mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jun  4 12:28:00 2011
     Raid Level : raid1
     Array Size : 1951945600 (1861.52 GiB 1998.79 GB)
  Used Dev Size : 1951945600 (1861.52 GiB 1998.79 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jun 30 20:12:20 2012
          State : clean, degraded, recovering
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 14% complete

           UUID : 988c992e:7278db96:507d8570:835cbc81
         Events : 0.73011

    Number   Major   Minor   RaidDevice State
       2       8        3        0      spare rebuilding   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3

So, as far as I can tell, the raid itself is fine, the disks are ok, but the partition information for /dev/md0 is wrong.

Which makes the question: can I correct the information without wiping everything on the disks?

---

