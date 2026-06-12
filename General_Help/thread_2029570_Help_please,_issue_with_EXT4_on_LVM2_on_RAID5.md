---
title: "Help please, issue with EXT4 on LVM2 on RAID5"
date: 2012-07-19
forum: General Help
---

### Post by jostrus on 2012-07-19
First off I want to apologize if this is in the wrong place I couldn't really find a better place to start this post.

That said here's the quick and dirty of my problem. I'm using Lubuntu 12.04, Xubuntu 12.04 and plain Ubuntu 12.04. Tried with generic kernels 3.2.0-25 and 3.2.0-26. This issue persists on all 3 variants which are on 3 different computers. I built the raid once and just moved the drives to the other computers for trial testing, recreating the pv/vg/lv each time on the new computer incase there was some issue with a kernel or some weird thing. I've tried using both EXT4 and XFS on a LVM2 logical volume which is on a linux dm software raid. Configuration to follow. Immediately after doing the mkfs running an fsck/xfs_check fails miserably. Found this out after taking time to initially fill the volume with test data. Going forth I will refer strictly to the EXT4 results as that is my preferred file system. Hopefully someone can shed light onto what's going wrong, or if I'm doing something wrong somewhere, or if there might be a bug somewhere.

The Raid5 consists of (4x) 1.5TB USB hard drives partitioned via GPT and using the partitions as the raid devices
```
root@nasbackup:~# for part in d e f g; do parted /dev/sd$part unit s print; done
Model: WD 15EADS External (scsi)
Disk /dev/sdd: 2930277168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name                           Flags
1      2048s  2928175104s  2928173057s               raid - storage_backup - dev 0  raid

Model: WD 15EADS External (scsi)
Disk /dev/sde: 2930277168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name                           Flags
1      2048s  2928175104s  2928173057s               raid - storage_backup - dev 1  raid

Model: WD Ext HDD 1021 (scsi)
Disk /dev/sdf: 2930272256s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name                           Flags
1      2048s  2928175104s  2928173057s               raid - storage_backup - dev 2  raid

Model: Maxtor OneTouch (scsi)
Disk /dev/sdg: 2930277168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name                           Flags
1      2048s  2928175104s  2928173057s               raid - storage_backup - dev 3  raid

root@nasbackup:~# mdadm -D /dev/md/storage_backup
/dev/md/storage_backup:
        Version : 1.2
  Creation Time : Fri Jul 13 18:26:34 2012
     Raid Level : raid5
     Array Size : 4392254976 (4188.78 GiB 4497.67 GB)
  Used Dev Size : 1464084992 (1396.26 GiB 1499.22 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Thu Jul 19 18:16:40 2012
          State : active
Active Devices : 4
Working Devices : 4
Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : nasbackup:storage_backup  (local to host nasbackup)
           UUID : 2d23d3bf:dead6278:7c7cbf74:b1c308b4
         Events : 108635

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1
       2       8       81        2      active sync   /dev/sdf1
       4       8       97        3      active sync   /dev/sdg1

```

The raid itself doesn't seem to be an issue as I tried putting the file system directly on the md device and there was no apparent issue until after the LVM layers were applied. I created using 128MB extents instead of the default 4MB as I read somewhere that lvm2 had some issue with more than 65k extent counts. I tried 4MB, 16MB, 32MB, 64MB, and 128MB just for giggles but had the same results.
```
root@nasbackup:~# pvcreate --verbose /dev/md/storage_backup
    Set up physical volume for "/dev/md/storage_backup" with 8784509952 available sectors
    Zeroing start of device /dev/md/storage_backup
  Physical volume "/dev/md/storage_backup" successfully created
root@nasbackup:~# vgcreate --verbose -s 128M vg_storage_backup /dev/md/storage_backup
    Wiping cache of LVM-capable devices
    Wiping cache of LVM-capable devices
    Adding physical volume '/dev/md/storage_backup' to volume group 'vg_storage_backup'
    Archiving volume group "vg_storage_backup" metadata (seqno 0).
    Creating volume group backup "/etc/lvm/backup/vg_storage_backup" (seqno 1).
  Volume group "vg_storage_backup" successfully created

root@nasbackup:~# vgdisplay vg_storage_backup
  --- Volume group ---
  VG Name               vg_storage_backup
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  1
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               4.09 TiB
  PE Size               128.00 MiB
  Total PE              33510
  Alloc PE / Size       0 / 0
  Free  PE / Size       33510 / 4.09 TiB
  VG UUID               eDm02A-PmI0-67my-Gxfd-helQ-MJGv-r61Nb3
root@nasbackup:~# lvcreate  --verbose --extents 100%FREE  --name lv_storage_backup vg_storage_backup
    Setting logging type to disk
    Finding volume group "vg_storage_backup"
    Archiving volume group "vg_storage_backup" metadata (seqno 1).
    Creating logical volume lv_storage_backup
    Creating volume group backup "/etc/lvm/backup/vg_storage_backup" (seqno 2).
    Found volume group "vg_storage_backup"
    Creating vg_storage_backup-lv_storage_backup
    Loading vg_storage_backup-lv_storage_backup table (252:0)
    Resuming vg_storage_backup-lv_storage_backup (252:0)
    Clearing start of logical volume "lv_storage_backup"
    Creating volume group backup "/etc/lvm/backup/vg_storage_backup" (seqno 2).
  Logical volume "lv_storage_backup" created
root@nasbackup:~# lvdisplay /dev/vg_storage_backup/lv_storage_backup
  --- Logical volume ---
  LV Name                /dev/vg_storage_backup/lv_storage_backup
  VG Name                vg_storage_backup
  LV UUID                hbYfbR-4hFn-rxGK-VoQ2-S4uw-d5us-alAUoz
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                4.09 TiB
  Current LE             33510
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     6144
  Block device           252:0
root@nasbackup:~# mkfs.ext4 -m 0 -L "storage_backup" -T largefile /dev/md/storage_backup
mke2fs 1.42 (29-Nov-2011)
Filesystem label=storage_backup
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=128 blocks, Stripe width=384 blocks
4289408 inodes, 1098063744 blocks
0 blocks (0.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
33511 block groups
32768 blocks per group, 32768 fragments per group
128 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848, 512000000, 550731776, 644972544

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

```

So far so good until
```
root@nasbackup:~# fsck.ext4 -vfy /dev/vg_storage_backup/lv_storage_backup
e2fsck 1.42 (29-Nov-2011)
fsck.ext4: Group descriptors look bad... trying backup blocks...
One or more block group descriptor checksums are invalid.  Fix? yes

Group descriptor 0 checksum is invalid.  FIXED.
Group descriptor 1 checksum is invalid.  FIXED.
Group descriptor 2 checksum is invalid.  FIXED.
Group descriptor 3 checksum is invalid.  FIXED.
Group descriptor 4 checksum is invalid.  FIXED.
Group descriptor 5 checksum is invalid.  FIXED.
Group descriptor 6 checksum is invalid.  FIXED.
Group descriptor 7 checksum is invalid.  FIXED.
Group descriptor 8 checksum is invalid.  FIXED.
Group descriptor 9 checksum is invalid.  FIXED.
Group descriptor 10 checksum is invalid.  FIXED.
Group descriptor 11 checksum is invalid.  FIXED.
Group descriptor 12 checksum is invalid.  FIXED.
Group descriptor 13 checksum is invalid.  FIXED.
--------SNIP----------
Group descriptor 33509 checksum is invalid.  FIXED.
Pass 1: Checking inodes, blocks, and sizes
Group 9976's inode table at 326631520 conflicts with some other fs block.
Relocate? yes

Group 9976's block bitmap at 326631432 conflicts with some other fs block.
Relocate? yes

Group 9976's inode bitmap at 326631448 conflicts with some other fs block.
Relocate? yes

Group 9977's inode table at 326631528 conflicts with some other fs block.
Relocate? yes

Group 9977's block bitmap at 326631433 conflicts with some other fs block.
Relocate? yes

Group 9977's inode bitmap at 326631449 conflicts with some other fs block.
Relocate? yes

-----SNIP------

Inode 493088 is in use, but has dtime set.  Fix? yes

Inode 493088 has imagic flag set.  Clear? yes

Inode 493088 has a extra size (65535) which is invalid
Fix? yes

Inode 493088 has compression flag set on filesystem without compression support.  Clear? yes

Inode 493088 has INDEX_FL flag set but is not a directory.
Clear HTree index? yes

Inode 493088 should not have EOFBLOCKS_FL set (size 18446744073709551615, lblk -1)
Clear? yes

Inode 493088, i_size is 18446744073709551615, should be 0.  Fix? yes

Inode 493088, i_blocks is 281474976710655, should be 0.  Fix? yes

Inode 514060 has an invalid extent node (blk 131629062, lblk 0)
Clear? yes

fsck.ext4: e2fsck_read_bitmaps: illegal bitmap block(s) for storage_backup

storage_backup: ***** FILE SYSTEM WAS MODIFIED *****
e2fsck: aborted

storage_backup: ***** FILE SYSTEM WAS MODIFIED *****

```
It doesn't even finish it aborts itself. If I run the fsck again I get the exact same errors as if it doesn't actually modify the file system like it says it did.

Incase it matters the results directly on the md device
```
root@nasbackup:~# mkfs.ext4 -m 0 -L "storage_backup" -T largefile /dev/md/storage_backup
mke2fs 1.42 (29-Nov-2011)
Filesystem label=storage_backup
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=128 blocks, Stripe width=384 blocks
4289408 inodes, 1098063744 blocks
0 blocks (0.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
33511 block groups
32768 blocks per group, 32768 fragments per group
128 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848, 512000000, 550731776, 644972544

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

root@nasbackup:~# fsck.ext4 -vfy /dev/md/storage_backup
e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      11 inodes used (0.00%)
       0 non-contiguous files (0.0%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 3
  390434 blocks used (0.04%)
       0 bad blocks
       1 large file

       0 regular files
       2 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
       2 files

```

---

### Post by jostrus on 2012-07-29
Seems I may have resolved my problem. Turns out if I put the file system directly on the raid md device it also failed, just not right away. I ran badblocks with the -n for non destructive testing and found out data wasn't being written/read properly and narrowed it down to one of the hard drives. After removing said hard drive the whole mess started working properly.

---

