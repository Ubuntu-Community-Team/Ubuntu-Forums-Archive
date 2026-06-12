---
title: "&quot;Disk too small&quot; testdisk problem"
date: 2012-09-14
forum: General Help
---

### Post by Laski on 2012-09-14
Hi and sorry for my bad english! Long story made short, I used testdisk to recover a partition -that's called wineprefix, that haves windows games for use them in linux- but by inexpertise selected all the others partitions as deleted. When I realised the problem, I ran testdisk again, but heres the situation:
[http://img525.imageshack.us/img525/7958/captura01j.png](http://img525.imageshack.us/img525/7958/captura01j.png)
[http://img198.imageshack.us/img198/7489/captura02v.png](http://img198.imageshack.us/img198/7489/captura02v.png)
As you can see, I can't recover my "Home" partition, wich is very important for me. Other partitions are OK, and I've already made a backup of them so I cant play with what is left.
What I've tried: set the cilinders artificially to 124604 so testdisk could try to read the partitions, and then I could copy the contents to another disk and then exit without actually writing the bad geometry to disk (don't blame me if thats a stupid idea, I read that from [here]("http://forum.cgsecurity.org/phpBB3/post3435.html#p3435")). But...

```
Fri Jul 27 05:31:42 2012
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 3.0.0-22-generic (#36-Ubuntu SMP Tue Jun 12 17:13:04 UTC 2012)
Compiler: GCC 4.5 - Oct 17 2010 20:12:36
ext2fs lib: 1.41.14, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       312581808 sectors
/dev/sda: user_max   312581808 sectors
/dev/sda: native_max 312581808 sectors
/dev/sda: dco        312581808 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       1953525168 sectors
/dev/sdb: user_max   1953525168 sectors
/dev/sdb: native_max 1953525168 sectors
/dev/sdb: dco        1953525168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
/dev/sr0 is not an ATA disk
Hard disk list
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512 - ATA Maxtor 6V160E0
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - ATA ST31000333AS
Disk /dev/sdc - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - Generic External
Disk /dev/sdd - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512 - WD 1600BEV External
Disk /dev/sr0 - 190 MB / 181 MiB - CHS 92867 1 1 (RO), sector size=2048 - HL-DT-ST DVDRAM GH20NS15

Partition table type (auto): Intel
Disk /dev/sdb - 1000 GB / 931 GiB - ATA ST31000333AS
Partition table type: Intel
New geometry
Disk /dev/sdb - 1024 GB / 954 GiB - CHS 124605 255 63 sector_size=512

Analyse Disk /dev/sdb - 1024 GB / 954 GiB - CHS 124605 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
NTFS at 19582/1/1
get_geometry_from_list_part_aux head=255 nbr=3
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=3
Current partition structure:
 1 P HPFS - NTFS              0   1  1 19581 254 63  314584767
 2 P HPFS - NTFS          19582   1  1 95492 129 51 1219502265 [shared]
 3 P Linux                96145  88  8 98103 120  1   31457280
No partition is bootable
Backup partition structure
partition_save
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sdb - 1024 GB / 954 GiB - CHS 124605 255 63
NTFS at 0/1/1
filesystem size           314584767
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1 19581 254 63  314584767
     NTFS, 161 GB / 150 GiB
NTFS at 19582/1/1
filesystem size           1219502265
sectors_per_cluster       8
mft_lcn                   88146816
mftmirr_lcn               4411315
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          19582   1  1 95492 129 51 1219502265 [shared]
     NTFS, 624 GB / 581 GiB
     Linux Swap           95492 162 31 96145  87 54   10485744
     SWAP2 version 1, 5368 MB / 5119 MiB

recover_EXT2: s_block_group_nr=0/120, s_mnt_count=9/37, s_blocks_per_group=32768, s_inodes_per_group=8208
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 3932160
recover_EXT2: part_size 31457280
     Linux                96145  88  8 98103 120  1   31457280
     EXT4 Large file Sparse superblock, 16 GB / 15 GiB

recover_EXT2: s_block_group_nr=0/1440, s_mnt_count=10/31, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 47185920
recover_EXT2: part_size 377487360
     Linux                101060  74  7 124557 201 60  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
get_geometry_from_list_part_aux head=255 nbr=3
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=3

Results
   * HPFS - NTFS              0   1  1 19581 254 63  314584767
     NTFS, 161 GB / 150 GiB
   P HPFS - NTFS          19582   1  1 95492 129 51 1219502265 [shared]
     NTFS, 624 GB / 581 GiB
   P Linux Swap           95492 162 31 96145  87 54   10485744
     SWAP2 version 1, 5368 MB / 5119 MiB
   L Linux                96145  88  8 98103 120  1   31457280
     EXT4 Large file Sparse superblock, 16 GB / 15 GiB
   L Linux                101060  74  7 124557 201 60  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB


dir_partition inode=2
   L Linux                101060  74  7 124557 201 60  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 2133571387.
Directory /

interface_write()
 1 * HPFS - NTFS              0   1  1 19581 254 63  314584767
 2 P HPFS - NTFS          19582   1  1 95492 129 51 1219502265 [shared]
 3 P Linux Swap           95492 162 31 96145  87 54   10485744
 4 E extended LBA         96145  88  1 124604 254 63  457204356
 5 L Linux                96145  88  8 98103 120  1   31457280
 6 L Linux                101060  74  7 124557 201 60  377487360 [Home]

search_part()
Disk /dev/sdb - 1024 GB / 954 GiB - CHS 124605 255 63
NTFS at 0/1/1
filesystem size           314584767
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1 19581 254 63  314584767
     NTFS, 161 GB / 150 GiB
NTFS at 13055/15/16
filesystem size           209729465
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               19661547
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  9 13055  15 16  209729465
     NTFS found using backup sector!, 107 GB / 100 GiB

recover_EXT2: s_block_group_nr=0/399, s_mnt_count=17/35, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 13106432
recover_EXT2: part_size 104851456
     Linux                16207  79  1 22734   2 52  104851456 [wineprefix]
     EXT4 Large file Sparse superblock Recover, 53 GB / 49 GiB

recover_EXT2: s_block_group_nr=0/399, s_mnt_count=17/35, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 13106432
recover_EXT2: part_size 104851456
     Linux                16210   2  1 22736 180 52  104851456 [wineprefix]
     EXT4 Large file Sparse superblock Recover, 53 GB / 49 GiB
NTFS at 19581/254/63
filesystem size           314584767
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1 19581 254 63  314584767
     NTFS found using backup sector!, 161 GB / 150 GiB
NTFS at 19582/1/1
filesystem size           1219502265
sectors_per_cluster       8
mft_lcn                   88146816
mftmirr_lcn               4411315
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          19582   1  1 95492 129 51 1219502265 [shared]
     NTFS, 624 GB / 581 GiB
NTFS at 94839/171/52
filesystem size           1209014457
sectors_per_cluster       8
mft_lcn                   88146816
mftmirr_lcn               4411315
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          19582   1 11 94839 171 52 1209014457
     NTFS found using backup sector!, 619 GB / 576 GiB
NTFS at 95492/129/61
filesystem size           1219502265
sectors_per_cluster       8
mft_lcn                   88146816
mftmirr_lcn               4411315
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          19582   1 11 95492 129 61 1219502265
     NTFS found using backup sector!, 624 GB / 581 GiB
     Linux Swap           95492 162 31 96145  87 54   10485744
     SWAP2 version 1, 5368 MB / 5119 MiB
NTFS at 96145/55/38
filesystem size           20971513
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               655648
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          94839 204 29 96145  55 38   20971513
     NTFS found using backup sector!, 10737 MB / 10239 MiB
NTFS at 96145/88/7
filesystem size           20973561
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               655648
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          94839 204 29 96145  88  7   20973561
     NTFS found using backup sector!, 10 GB / 10 GiB

recover_EXT2: s_block_group_nr=0/120, s_mnt_count=9/37, s_blocks_per_group=32768, s_inodes_per_group=8208
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 3932160
recover_EXT2: part_size 31457280
     Linux                96145  88  8 98103 120  1   31457280
     EXT4 Large file Sparse superblock, 16 GB / 15 GiB

recover_EXT2: s_block_group_nr=0/120, s_mnt_count=34/37, s_blocks_per_group=32768, s_inodes_per_group=8208
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 3932160
recover_EXT2: part_size 31457280
     Linux                96951 203 21 98909 235 14   31457280
     EXT4 Large file Sparse superblock Recover, 16 GB / 15 GiB

recover_EXT2: s_block_group_nr=0/1440, s_mnt_count=10/31, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 47185920
recover_EXT2: part_size 377487360
     Linux                101060  74  7 124557 201 60  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB

recover_EXT2: s_block_group_nr=0/1440, s_mnt_count=10/31, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 47185920
recover_EXT2: part_size 377487360
     Linux                101061  46 42 124558 174 32  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB

recover_EXT2: s_block_group_nr=0/1440, s_mnt_count=10/31, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 47185920
recover_EXT2: part_size 377487360
     Linux                101069 184 44 124567  57 34  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB

recover_EXT2: s_block_group_nr=0/1440, s_mnt_count=10/31, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 47185920
recover_EXT2: part_size 377487360
     Linux                101080 110 23 124577 238 13  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB

recover_EXT2: s_block_group_nr=0/1440, s_mnt_count=10/31, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 47185920
recover_EXT2: part_size 377487360
     Linux                101104   4 21 124601 132 11  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB

recover_EXT2: s_block_group_nr=0/1440, s_mnt_count=10/31, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 47185920
recover_EXT2: part_size 377487360
     Linux                101105 139 27 124603  12 17  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
     Linux Swap           110949 247 19 111015  61  6    1048560
     SWAP2 version 1, 536 MB / 511 MiB
NTFS at 0/1/1
filesystem size           314584767
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
NTFS at 19582/1/1
filesystem size           1219502265
sectors_per_cluster       8
mft_lcn                   88146816
mftmirr_lcn               4411315
clusters_per_mft_record   -10
clusters_per_index_record 1
NTFS at 19582/1/1
filesystem size           1219502265
sectors_per_cluster       8
mft_lcn                   88146816
mftmirr_lcn               4411315
clusters_per_mft_record   -10
clusters_per_index_record 1
get_geometry_from_list_part_aux head=255 nbr=3
get_geometry_from_list_part_aux head=8 nbr=3
get_geometry_from_list_part_aux head=16 nbr=3
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=2
get_geometry_from_list_part_aux head=128 nbr=2
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=3

Results
     HPFS - NTFS              0   1  1 19581 254 63  314584767
     NTFS, 161 GB / 150 GiB
     HPFS - NTFS              0   1  9 13055  15 16  209729465
     NTFS found using backup sector!, 107 GB / 100 GiB
     Linux                16207  79  1 22734   2 52  104851456 [wineprefix]
     EXT4 Large file Sparse superblock Recover, 53 GB / 49 GiB
     Linux                16210   2  1 22736 180 52  104851456 [wineprefix]
     EXT4 Large file Sparse superblock Recover, 53 GB / 49 GiB
     HPFS - NTFS          19582   1  1 95492 129 51 1219502265 [shared]
     NTFS, 624 GB / 581 GiB
     HPFS - NTFS          19582   1 11 94839 171 52 1209014457
     NTFS found using backup sector!, 619 GB / 576 GiB
     HPFS - NTFS          19582   1 11 95492 129 61 1219502265
     NTFS found using backup sector!, 624 GB / 581 GiB
     HPFS - NTFS          94839 204 29 96145  55 38   20971513
     NTFS found using backup sector!, 10737 MB / 10239 MiB
     HPFS - NTFS          94839 204 29 96145  88  7   20973561
     NTFS found using backup sector!, 10 GB / 10 GiB
     Linux Swap           95492 162 31 96145  87 54   10485744
     SWAP2 version 1, 5368 MB / 5119 MiB
     Linux                96145  88  8 98103 120  1   31457280
     EXT4 Large file Sparse superblock, 16 GB / 15 GiB
     Linux                96951 203 21 98909 235 14   31457280
     EXT4 Large file Sparse superblock Recover, 16 GB / 15 GiB
     Linux                101060  74  7 124557 201 60  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
     Linux                101061  46 42 124558 174 32  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
     Linux                101069 184 44 124567  57 34  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
     Linux                101080 110 23 124577 238 13  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
     Linux                101104   4 21 124601 132 11  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
     Linux                101105 139 27 124603  12 17  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
     Linux Swap           110949 247 19 111015  61  6    1048560
     SWAP2 version 1, 536 MB / 511 MiB


[B]dir_partition inode=2
     Linux                101060  74  7 124557 201 60  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 2133571387.
Directory /


dir_partition inode=2
     Linux                101061  46 42 124558 174 32  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 2133571387.
Directory /


dir_partition inode=2
     Linux                101069 184 44 124567  57 34  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 1.
Directory /


dir_partition inode=2
     Linux                101080 110 23 124577 238 13  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 1.
Directory /


dir_partition inode=2
     Linux                101104   4 21 124601 132 11  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 2133571402.
Directory /


dir_partition inode=2
     Linux                101105 139 27 124603  12 17  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 2133571402.
Directory /


dir_partition inode=2
     Linux                101104   4 21 124601 132 11  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 2133571402.
Directory /


dir_partition inode=2
     Linux                101080 110 23 124577 238 13  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 1.
Directory /


dir_partition inode=2
     Linux                101069 184 44 124567  57 34  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 1.
Directory /


dir_partition inode=2
     Linux                101061  46 42 124558 174 32  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 2133571387.
Directory /


dir_partition inode=2
     Linux                101060  74  7 124557 201 60  377487360 [Home]
     EXT4 Large file Sparse superblock Recover, 193 GB / 180 GiB
ext2fs_dir_iterate failed with error 2133571387.
Directory /
[/B]
interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition
Partition table type (auto): Intel
Disk /dev/sda - 160 GB / 149 GiB - ATA Maxtor 6V160E0
Partition table type: Intel

Analyse Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
heads/cylinder 4 (NTFS) != 255 (HD)
sect/track 17 (NTFS) != 63 (HD)
NTFS at 13056/1/1
Info: size boot_sector 102835385, partition 102848067
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=4
get_geometry_from_list_part_aux head=16 nbr=4
get_geometry_from_list_part_aux head=32 nbr=4
get_geometry_from_list_part_aux head=64 nbr=4
get_geometry_from_list_part_aux head=128 nbr=4
get_geometry_from_list_part_aux head=240 nbr=4
get_geometry_from_list_part_aux head=255 nbr=6
Current partition structure:
Warning: Incorrect number of heads/cylinder 4 (NTFS) != 255 (HD)
Warning: Incorrect number of sectors per track 17 (NTFS) != 63 (HD)
 1 * HPFS - NTFS              0   1  1 13055 254 63  209744577 [Ex XP]
 2 E extended LBA         13056   0  1 19457 254 63  102848130
 5 L HPFS - NTFS          13056   1  1 19457 254 63  102848067
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
NTFS at 0/1/1
heads/cylinder 4 (NTFS) != 255 (HD)
sect/track 17 (NTFS) != 63 (HD)
filesystem size           209744577
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1 13055 254 63  209744577 [Ex XP]
     NTFS, 107 GB / 100 GiB
NTFS at 13056/1/1
filesystem size           102835385
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               6425996
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          13056   1  1 19457  53 44  102835385
     NTFS, 52 GB / 49 GiB
get_geometry_from_list_part_aux head=255 nbr=3
get_geometry_from_list_part_aux head=8 nbr=3
get_geometry_from_list_part_aux head=16 nbr=3
get_geometry_from_list_part_aux head=32 nbr=3
get_geometry_from_list_part_aux head=64 nbr=3
get_geometry_from_list_part_aux head=128 nbr=3
get_geometry_from_list_part_aux head=240 nbr=3
get_geometry_from_list_part_aux head=255 nbr=3

Results
   * HPFS - NTFS              0   1  1 13055 254 63  209744577 [Ex XP]
     NTFS, 107 GB / 100 GiB
   L HPFS - NTFS          13056   1  1 19457 254 63  102848067
     NTFS, 52 GB / 49 GiB

interface_write()
 1 P HPFS - NTFS              0   1  1 13055 254 63  209744577 [Ex XP]
 2 * HPFS - NTFS          13056   1  1 19457 254 63  102848067
write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition
You will have to reboot for the change to take effect.
New options :
 Dump : No
 Cylinder boundary : Yes
 Allow partial last cylinder : No
 Expert mode : No

TestDisk exited normally.
```It recognized the -possible- partitions but could read none. I'm very confused now, and I would aprecciate every hint that you can give to me. I saw similar problems here in this forum but with very particular situations, and I don't know exactly how to 'transpolate' the solution (and obviously don't want to mess things up even more). I also posted this in cgsecurity.org forums (the creator of testdisk) but at the time they didn't told me nothing new, I have read both and think this is better in terms of answer times and expertise of the people.
I know the files are there, I won't give up until I have recovered them. With your help, I hope we'll can :p.

Thank you so much!

---

### Post by Laski on 2012-09-14
If it's of any help, here are the threads I looked that seemed to have a similar problem:

[http://ubuntuforums.org/showthread.php?t=1667614&page=4](http://ubuntuforums.org/showthread.php?t=1667614&page=4)
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)
[http://ubuntuforums.org/showthread.php?p=10470033](http://ubuntuforums.org/showthread.php?p=10470033)
[http://ubuntuforums.org/showthread.php?t=2013581](http://ubuntuforums.org/showthread.php?t=2013581)

---

### Post by Laski on 2012-09-18
Up!

---

