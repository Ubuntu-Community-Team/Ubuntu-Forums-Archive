---
title: "partition table repair"
date: 2010-02-21
forum: General Help
---

### Post by KhaaL on 2010-02-21
A friend of mine had his partitions go fubar on his harddrive after he updated ubuntu. The details of how it could actually happen were unclear, but i decided to help him repair the partitions. it contained two partitions, one small containing FAT32 and a bigger one containing ext3. the ext3 partition is unmountable with the error message "Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdj1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"


Since this is the first time i do it, i tried to read up on it and came across TestDisk. I ran it on the harddisk and a normal search this came up:

```
Disk /dev/sdj - 500 GB / 465 GiB - CHS 60801 255 63

The harddisk (500 GB / 465 GiB) seems too small! (< 1000 GB / 931 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  HPFS - NTFS          60800 254 63 121601 253 61  976768001

```

After a deep search, it found the ext3 partition and i marked the ntfs with delete flag and primary flag on the ext3. Afterwards i decided to run fsck through gparted with were also unsucessful:

```
GParted 0.4.5

Libparted 1.8.8.1.159-1e0e

Check and repair file system (ext3) on /dev/sdj1  00:00:00    ( ERROR )
        
calibrate /dev/sdj1  00:00:00    ( SUCCESS )
        
path: /dev/sdj1
start: 63
end: 976559219
size: 976559157 (465.66 GiB)
check file system on /dev/sdj1 for errors and (if possible) fix them  00:00:00    ( ERROR )
        
e2fsck -f -y -v /dev/sdj1
        
e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck: going back to original superblock
Filesystem mounted or opened exclusively by another program?
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Bad magic number in super-block when using the backup blocks
e2fsck: Device or resource busy while trying to open /dev/sdj1
========================================
```

The error message that the device is busy comes up even though the partitions are unmounted. Right now i still can't get the ext3 partition working, and i'm out of clues. how should i proceed? the partition table currently looks:


```
No EXT2, JFS, Reiser, cramfs or XFS marker
 1 P Linux                    0   1  1 60787 254 63  976559157
 1 P Linux                    0   1  1 60787 254 63  976559157
 2 P FAT32 LBA            60788   0  1 60800 254 63     208845 [LILTOUCH]
No partition is bootable



[ Continue ]
NTFS, 500 GB / 465 GiB

```

and the output from dmesg | tail:

```
[62329.080884] sd 11:0:0:0: [sdj] Assuming drive cache: write through
[62329.080894]  sdj: sdj1 sdj2
[62329.092862] sd 11:0:0:0: [sdj] Assuming drive cache: write through
[62329.092876] sd 11:0:0:0: [sdj] Attached SCSI disk
[62330.232410] EXT3-fs error (device sdj1): ext3_check_descriptors: Block bitmap for group 2816 not in group (block 989657561)!
[62330.233083] EXT3-fs: group descriptors corrupted!
[62336.699731] EXT3-fs error (device sdj1): ext3_check_descriptors: Block bitmap for group 2816 not in group (block 989657561)!
[62336.701148] EXT3-fs: group descriptors corrupted!
[62912.897298] EXT3-fs error (device sdj1): ext3_check_descriptors: Block bitmap for group 2816 not in group (block 989657561)!
[62912.898216] EXT3-fs: group descriptors corrupted!
```

---

