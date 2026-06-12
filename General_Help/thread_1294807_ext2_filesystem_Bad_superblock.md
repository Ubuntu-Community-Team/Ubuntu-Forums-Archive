---
title: "ext2 filesystem: Bad superblock"
date: 2009-10-18
forum: General Help
---

### Post by roland_j on 2009-10-18
Hi,

just another problem with a bad superblock: I cannot mount a partition with an ext2 fs on it. It worked fine and I dont know what happened.

```
fsck /dev/sda5
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Group descriptors look bad... trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

Here is some information about my system:

```
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x552d552d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12160    97675168+   7  HPFS/NTFS
/dev/sda2           12161       30401   146520832+   5  Extended
/dev/sda5           12161       29915   142617006   83  Linux
/dev/sda6           29916       30401     3903763+  82  Linux swap / Solaris

```

Trying to mount failed:
```

sudo dmesg | tail
[ 1015.390357] usb 1-1: USB disconnect, address 2
[ 1091.999126] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[ 1091.999346] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1102.780073] eth0: no IPv6 routers present
[ 1881.178002] EXT2-fs error (device sda5): ext2_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
[ 1881.178017] EXT2-fs: group descriptors corrupted!
[ 1961.810131] EXT2-fs error (device sda5): ext2_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
[ 1961.810139] EXT2-fs: group descriptors corrupted!
[ 2100.847466] EXT2-fs error (device sda5): ext2_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
[ 2100.847481] EXT2-fs: group descriptors corrupted!

```

I ran testdisk and got this log file:

```
cat testdisk.log 


Sun Oct 18 22:28:55 2009
Command line: TestDisk

TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.28-11-generic (#42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009)
Compiler: GCC 4.3 - May  6 2009 14:40:08
ext2fs lib: 1.41.4, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       488397168 sectors
/dev/sda: user_max   488397168 sectors
/dev/sda: native_max 488397168 sectors
/dev/sda: dco        488397168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
/dev/sr0 is not an ATA disk
Hard disk list
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512 - ATA WDC WD2500BEVS-2
Disk /dev/sr0 - 732 MB / 698 MiB - CHS 357866 1 1 (RO), sector size=2048 - MATSHITA DVD-RAM UJ-860S

Partition table type (auto): Intel
Disk /dev/sda - 250 GB / 232 GiB - ATA WDC WD2500BEVS-2
Partition table type: Intel

Interface Advanced
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
get_geometry_from_list_part_aux head=255 nbr=10
get_geometry_from_list_part_aux head=8 nbr=4
get_geometry_from_list_part_aux head=16 nbr=4
get_geometry_from_list_part_aux head=32 nbr=4
get_geometry_from_list_part_aux head=64 nbr=4
get_geometry_from_list_part_aux head=128 nbr=4
get_geometry_from_list_part_aux head=240 nbr=4
get_geometry_from_list_part_aux head=255 nbr=10
 1 * HPFS - NTFS              0   1  1 12159 254 63  195350337
     NTFS, 100 GB / 93 GiB
 2 E extended             12160   0  1 30400 254 63  293041665
 5 L Linux                12160   1  1 29914 254 63  285234012
     EXT2 Large file Sparse superblock, 146 GB / 136 GiB
   X extended             29915   0  1 30400 254 63    7807590
 6 L Linux Swap           29915   1  1 30400 254 63    7807527
     SWAP2 version 1, 3997 MB / 3812 MiB
search_superblock

recover_EXT2: s_block_group_nr=0/1088, s_mnt_count=10/30, s_blocks_per_group=32768, s_inodes_per_group=16384
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35654251
recover_EXT2: part_size 285234008
Ext2 superblock found at sector 2 (block=0, blocksize=4096)
  Linux                12160   1  1 29914 254 59  285234008
superblock 0, blocksize=4096 []

TestDisk exited normally.

```

What superblock can I give fsck now for the -b option?

Regards
Roland

---

### Post by falconindy on 2009-10-18
I think your answer is right in your first code block.
> ```
fsck /dev/sda5
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Group descriptors look bad... trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    **e2fsck -b 8193 <device>**
```

---

### Post by roland_j on 2009-10-18
Hi,

e2fsck -b 8193 did not work. All other blocks (e.g. 16385, 24577, etc.) give the same message.

Any idea?

Regards
Roland

---

