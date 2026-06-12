---
title: "need help to rescue a mdadm RAID unable to mount"
date: 2011-04-28
forum: General Help
---

### Post by AllGamer on 2011-04-28
I originally commented on a similar topic [http://ubuntuforums.org/showthread.php?t=1736742](http://ubuntuforums.org/showthread.php?t=1736742)

but instead of hijacking somebody else topic to troubleshoot my own, I've decided to create my own.

so the problem some how started after a failed software update of my previous Ubuntu 10.10

ubuntu sits on its own IDE HDD and it became un-boot-able, so i simply went ahead and reinstalled ubuntu as it was a quick thing to do via USB media.

then i proceeded to run ```
sudo apt-get install mdadm
```, and proceed to assemble the RAID5, everything went smooth as expected (or so i though), but to my surprise when the system came up, it was reporting trouble mounting the volume with this error message.

**Error mounting volume**
An error ocurred while performing an operation on "on SATA" (whole-disk volume on 6.0 TB RAID-5 Array): Filesystem driver not installed

then on **Details** it shows:
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/md0, missing codepage or helper program, or other error
in some cases useful info is found in syslog -try dmesg | tail or so

and if i run **dmesg |tail** i get this output:

[66085.733117]  disk 0, o:1, dev:sdb
[66085.733119]  disk 1, o:1, dev:sdd
[66085.733122]  disk 2, o:1, dev:sdc
[66085.733125]  disk 3, o:1, dev:sde
[66085.733186] md0: detected capacity change from 0 to 6001196531712
[66085.733912]  md0:
[66109.049472] EXT3-fs error (device md0): ext3_check_descriptors: Block bitmap for group 1934 not in group (block 0)!
[66109.112479] EXT3-fs (md0): error: group descriptors corrupted
[66682.927915] EXT3-fs error (device md0): ext3_check_descriptors: Block bitmap for group 1934 not in group (block 0)!
[66682.991996] EXT3-fs (md0): error: group descriptors corrupted



the original format of mdadm RAID5 was EXT3
the volume name is "on SATA"
the mdadm RAID5 was on /dev/md0
it was composed of /dev/sdb /dev/sdd /dev/sdc /dev/sde


--- additional info ---
inside the **mdadm.conf** the only important line is this:

ARRAY /dev/md0 level=raid5 num-devices=4 UUID=1cd3c907:5ebd7927:310b5b34:c3d51354

all the other lines are default



--- out put from mdadm ---
sudo mdadm -Q -D /dev/md0
/dev/md0:
```

        Version : 00.90
  Creation Time : Tue Mar 15 19:12:55 2011
     Raid Level : raid5
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Apr 27 22:13:54 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1cd3c907:5ebd7927:310b5b34:c3d51354
         Events : 0.48

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       48        1      active sync   /dev/sdd
       2       8       32        2      active sync   /dev/sdc
       3       8       64        3      active sync   /dev/sde

```



is there any way to fix this and rescue my data? :confused:

---

### Post by piratebill on 2011-04-28
This might sounds really dumb, but did you try mounting the partition md0p1?

---

### Post by AllGamer on 2011-04-28
there is no md0p1, as in not partitioned via --audo=mdp, the raid was using the full 100% length of the HDD

that's why it was mounted as /dev/md0

---

### Post by fermulator on 2011-04-28
Yikes.  Yeah so you've got a RAID array created with "entire disks" without any "Linux RAID" partitions on them.  I don't believe this is recommended ... because probably what's happened is that the RAID superblock information has overridden a portion of the ext3 subsystem, or the ext3 filesystem has overridden the /dev/md0 RAID array.

Can you please report on the following commands?

```
cat /proc/mdstat
sudo fdisk -ul
sudo mdadm -E /dev/sd[bcde]
sudo mdadm -E /dev/sd[bcde]1

```

---

### Post by fermulator on 2011-04-28
Also, how did you assemble the array?

Just installed mdadm, then rebooted? (allowing mdadm to auto-assemble based on the entry in /etc/mdadm/mdadm.conf)

---

### Post by AllGamer on 2011-04-29
cat /proc/mdstat
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>

```

sudo fdisk -ul
```

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088bcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   307093503   153545728   83  Linux
/dev/sda2       307095550   320172031     6538241    5  Extended
/dev/sda5       307095552   320172031     6538240   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4f644f65

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4f644f63

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4f644f62

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4f644f64

   Device Boot      Start         End      Blocks   Id  System

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 4500.7 GB, 4500655964160 bytes
255 heads, 63 sectors/track, 547173 cylinders, total 8790343680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  4294967295  2147483647+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 4500.7 GB, 4500655964160 bytes
255 heads, 63 sectors/track, 547173 cylinders, total 8790343680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc1c38b7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1  4294967295  2147483647+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdh: 4500.7 GB, 4500655964160 bytes
256 heads, 63 sectors/track, 545036 cylinders, total 8790343680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5499b9a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1  4294967295  2147483647+  ee  GPT

```

sudo mdadm -E /dev/sd[bcde]
```

/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 06514154:ee223d2c:a8940a20:3aca4cc2 (local to host D945GNT)
  Creation Time : Thu Apr 28 22:32:17 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Apr 28 22:32:19 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 90e2b03b - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       64        1      active sync   /dev/sde
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 06514154:ee223d2c:a8940a20:3aca4cc2 (local to host D945GNT)
  Creation Time : Thu Apr 28 22:32:17 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Apr 28 22:32:19 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 90e2b04f - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       32        2      active sync   /dev/sdc

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       64        1      active sync   /dev/sde
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 06514154:ee223d2c:a8940a20:3aca4cc2 (local to host D945GNT)
  Creation Time : Thu Apr 28 22:32:17 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Apr 28 22:32:19 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 90e2b061 - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       48        3      active sync   /dev/sdd

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       64        1      active sync   /dev/sde
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sde:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 06514154:ee223d2c:a8940a20:3aca4cc2 (local to host D945GNT)
  Creation Time : Thu Apr 28 22:32:17 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Apr 28 22:32:19 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 90e2b06d - correct
         Events : 1

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       64        1      active sync   /dev/sde

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       64        1      active sync   /dev/sde
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd

```

sudo mdadm -E /dev/sd[bcde]1
```

mdadm: cannot open /dev/sd[bcde]1: No such file or directory

```

**re:** how did you assemble the array?
it was manually assembled with these parameters
```

sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde
mdadm: /dev/md0 has been started with 4 drives.

```

is there a way to recreate the superblocks like those other guys did on the other topic? [http://ubuntuforums.org/showthread.php?t=1736742](http://ubuntuforums.org/showthread.php?t=1736742)

also from the results of those commands, it appears only 2 disks have data, ideally if we could just mount those 2 disks, i can always copy the data elsewhere

---

### Post by AllGamer on 2011-04-30
help?... any one?

---

