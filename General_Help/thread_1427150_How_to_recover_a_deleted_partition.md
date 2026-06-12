---
title: "How to recover a deleted partition?"
date: 2010-03-11
forum: General Help
---

### Post by leorolla on 2010-03-11
Hello everyone,

Yesterday I was trying to get SGD running from a pendrive without success. Nothing was wrong with my PC, but I wanted an SGD just in case.

I ended up trying the "Smart BootManager" version 3.7 ( [http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/) ) listed by unetbootin.

From SmartBootManager I selected a given partition and chose "boot it", it asked whether I wanted to save it (sic), I said yes and after that I can't 
read my HD.

When booting, I have a grub-rescue> prompt, it knows I have (hd0) but it freezes when I try to look into it. That's all my PC is doing at the moment.

I have booted from a standard Karmic installation USB.

Following [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD) and [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
I have run:
sudo fdisk -l
sudo apt-get install testdisk
sudo testdisk
sudo apt-get install gpart
sudo gpart /dev/sda

Now fsdisk is reporting "This doesn't look like a partition table Probably you selected the wrong device."

And the starting/ending cylinders reported by fsdisk are different from those reported by testdisk and gpart

I remember that in the past I had problems after using gparted (not gpart), after resizing a given partition. It was solved by some brute-force 
method (like resizing the neighboring partition as well or something like that).

Is this natural to have a +1 cylinder difference between fsdisk and testdisk/gpart ?

What is the most safe way to recover it in this case ?

Logs are attached below.

Thanks a lot in advance!!!

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3ffd3ff

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1        3262    26201983+   7  HPFS/NTFS
/dev/sda2            3263       10717    59882287+   b  W95 FAT32
/dev/sda3           10718       14423    29768445   83  Linux
/dev/sda4           14424       14593     1365525   82  Linux swap / Solaris

Disk /dev/sdb: 8006 MB, 8006926336 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d3b5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         819     6578586    b  W95 FAT32
/dev/sdb2   *         820         952     1068322+  1b  Hidden W95 FAT32
/dev/sdb3             953         970      144585   1b  Hidden W95 FAT32
/dev/sdb4             971         973       24097+  16  Hidden FAT16
ubuntu@ubuntu:~$ fdisk -version
fdisk (util-linux-ng 2.16)
ubuntu@ubuntu:~$ 





ubuntu@ubuntu:~$ sudo gpart /dev/sda 

Begin scan...
Possible partition(Windows NT/W2K FS), size(25587mb), offset(0mb)
Possible partition(DOS FAT), size(58478mb), offset(25587mb)
Possible partition(Linux ext2), size(29070mb), offset(84066mb)
Possible partition(Linux swap), size(1333mb), offset(113137mb)
End scan.

Checking partitions...
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Partition(DOS or Windows 95 with 32 bit FAT, LBA): primary 
Partition(Linux ext2 filesystem): primary 
Partition(Linux swap or Solaris/x86): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 25587mb #s(52403952) s(63-52404014)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(3261/254/48)r

Primary partition(2)
   type: 012(0x0C)(DOS or Windows 95 with 32 bit FAT, LBA)
   size: 58478mb #s(119764575) s(52404030-172168604)
   chs:  (1023/254/63)-(1023/254/63)d (3262/0/1)-(10716/254/63)r

Primary partition(3)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 29070mb #s(59536888) s(172168605-231705492)
   chs:  (1023/254/63)-(1023/254/63)d (10717/0/1)-(14422/254/61)r

Primary partition(4)
   type: 130(0x82)(Linux swap or Solaris/x86)
   size: 1333mb #s(2731048) s(231705495-234436542)
   chs:  (1023/254/63)-(1023/254/63)d (14423/0/1)-(14592/254/61)r

ubuntu@ubuntu:~$ gpart -V
gpart v0.1h
ubuntu@ubuntu:~$ 






ubuntu@ubuntu:~$ testdisk --version
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
TestDisk exited normally.
ubuntu@ubuntu:~$



Print screens:



Version: 6.11
Compiler: GCC 4.4 - Jun 23 2009 17:11:34
ext2fs lib: 1.41.9, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
OS: Linux, kernel 2.6.31-14-generic (#48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009)
ubuntu@ubuntu:~$ sudo testdisk


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
 2 P FAT32                 3262   0  1 10716 254 63  119764575 [DATA]
 3 P Linux                10717   0  1 14422 254 63   59536890
 4 P Linux Swap           14423   0  1 14592 254 63    2731050









*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition



TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
P FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
P Linux                10717   0  1 14422 254 63   59536890
P Linux Swap           14423   0  1 14592 254 63    2731050








Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 26 GB / 24 GiB


ubuntu@ubuntu:~$ cat testdisk.log 


Thu Mar 11 11:47:20 2010
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.31-14-generic (#48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009)
Compiler: GCC 4.4 - Jun 23 2009 17:11:34
ext2fs lib: 1.41.9, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       234441648 sectors
/dev/sda: user_max   234441648 sectors
/dev/sda: native_max 234441648 sectors
/dev/sda: dco        234441648 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63, sector size=512 - ATA WDC WD1200BEVS-0
Disk /dev/sdb - 8006 MB / 7636 MiB - CHS 973 255 63, sector size=512 - Verbatim STORE N GO

Partition table type (auto): Intel
Disk /dev/sda - 120 GB / 111 GiB - ATA WDC WD1200BEVS-0
Partition table type: Intel

Analyse Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
Info: size boot_sector 52403953, partition 52403967
FAT32 at 3262/0/1
Info: size boot_sector 119764575, partition 119764575
FAT1 : 68-29300
FAT2 : 29301-58533
start_rootdir : 58566 root cluster : 3
Data : 58534-119764549
sectors : 119764575
cluster_size : 32
no_of_cluster : 3740813 (2 - 3740814)
fat_length 29233 calculated 29226
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8
Current partition structure:
 1 * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
 2 P FAT32                 3262   0  1 10716 254 63  119764575 [DATA]
 3 P Linux                10717   0  1 14422 254 63   59536890
 4 P Linux Swap           14423   0  1 14592 254 63    2731050
Backup partition structure
partition_save
Ask the user for vista mode
Computes LBA from CHS for Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
NTFS at 0/1/1
filesystem size           52403953
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               3276251
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1  3261 254 49   52403953 [WINDOWS]
     NTFS, 26 GB / 24 GiB
FAT32 at 3262/0/1
FAT1 : 68-29300
FAT2 : 29301-58533
start_rootdir : 58566 root cluster : 3
Data : 58534-119764549
sectors : 119764575
cluster_size : 32
no_of_cluster : 3740813 (2 - 3740814)
fat_length 29233 calculated 29226

FAT32 at 3262/0/1
     FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
     FAT32, 61 GB / 57 GiB

recover_EXT2: s_block_group_nr=0/227, s_mnt_count=19/30, s_blocks_per_group=32768, s_inodes_per_group=8176
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 7442111
recover_EXT2: part_size 59536888
     Linux                10717   0  1 14422 254 61   59536888
     EXT3 Large file Sparse superblock, 30 GB / 28 GiB
     Linux Swap           14423   0  1 14592 254 45    2731032
     SWAP2 version 1, 1398 MB / 1333 MiB
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8

Results
   * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
     NTFS, 26 GB / 24 GiB
   P FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
     FAT32, 61 GB / 57 GiB
   P Linux                10717   0  1 14422 254 63   59536890
     EXT3 Large file Sparse superblock, 30 GB / 28 GiB
   P Linux Swap           14423   0  1 14592 254 63    2731050
     SWAP2 version 1, 1398 MB / 1333 MiB

interface_write()
 1 * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
 2 P FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
 3 P Linux                10717   0  1 14422 254 63   59536890
 4 P Linux Swap           14423   0  1 14592 254 63    2731050
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

Analyse Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
Info: size boot_sector 52403953, partition 52403967
FAT32 at 3262/0/1
Info: size boot_sector 119764575, partition 119764575
FAT1 : 68-29300
FAT2 : 29301-58533
start_rootdir : 58566 root cluster : 3
Data : 58534-119764549
sectors : 119764575
cluster_size : 32
no_of_cluster : 3740813 (2 - 3740814)
fat_length 29233 calculated 29226
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8
Current partition structure:
 1 * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
 2 P FAT32                 3262   0  1 10716 254 63  119764575 [DATA]
 3 P Linux                10717   0  1 14422 254 63   59536890
 4 P Linux Swap           14423   0  1 14592 254 63    2731050
Ask the user for vista mode
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
NTFS at 0/1/1
filesystem size           52403953
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               3276251
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1  3261 254 49   52403953 [WINDOWS]
     NTFS, 26 GB / 24 GiB
FAT32 at 3262/0/1
FAT1 : 68-29300
FAT2 : 29301-58533
start_rootdir : 58566 root cluster : 3
Data : 58534-119764549
sectors : 119764575
cluster_size : 32
no_of_cluster : 3740813 (2 - 3740814)
fat_length 29233 calculated 29226

FAT32 at 3262/0/1
     FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
     FAT32, 61 GB / 57 GiB

recover_EXT2: s_block_group_nr=0/227, s_mnt_count=19/30, s_blocks_per_group=32768, s_inodes_per_group=8176
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 7442111
recover_EXT2: part_size 59536888
     Linux                10717   0  1 14422 254 61   59536888
     EXT3 Large file Sparse superblock, 30 GB / 28 GiB
     Linux Swap           14423   0  1 14592 254 45    2731032
     SWAP2 version 1, 1398 MB / 1333 MiB
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8

Results
   * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
     NTFS, 26 GB / 24 GiB
   P FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
     FAT32, 61 GB / 57 GiB
   P Linux                10717   0  1 14422 254 63   59536890
     EXT3 Large file Sparse superblock, 30 GB / 28 GiB
   P Linux Swap           14423   0  1 14592 254 63    2731050
     SWAP2 version 1, 1398 MB / 1333 MiB

interface_write()
 1 * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
 2 P FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
 3 P Linux                10717   0  1 14422 254 63   59536890
 4 P Linux Swap           14423   0  1 14592 254 63    2731050
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

Analyse Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
Info: size boot_sector 52403953, partition 52403967
FAT32 at 3262/0/1
Info: size boot_sector 119764575, partition 119764575
FAT1 : 68-29300
FAT2 : 29301-58533
start_rootdir : 58566 root cluster : 3
Data : 58534-119764549
sectors : 119764575
cluster_size : 32
no_of_cluster : 3740813 (2 - 3740814)
fat_length 29233 calculated 29226
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8
Current partition structure:
 1 * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
 2 P FAT32                 3262   0  1 10716 254 63  119764575 [DATA]
 3 P Linux                10717   0  1 14422 254 63   59536890
 4 P Linux Swap           14423   0  1 14592 254 63    2731050
Ask the user for vista mode
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
NTFS at 0/1/1
filesystem size           52403953
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               3276251
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1  3261 254 49   52403953 [WINDOWS]
     NTFS, 26 GB / 24 GiB
FAT32 at 3262/0/1
FAT1 : 68-29300
FAT2 : 29301-58533
start_rootdir : 58566 root cluster : 3
Data : 58534-119764549
sectors : 119764575
cluster_size : 32
no_of_cluster : 3740813 (2 - 3740814)
fat_length 29233 calculated 29226

FAT32 at 3262/0/1
     FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
     FAT32, 61 GB / 57 GiB

recover_EXT2: s_block_group_nr=0/227, s_mnt_count=19/30, s_blocks_per_group=32768, s_inodes_per_group=8176
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 7442111
recover_EXT2: part_size 59536888
     Linux                10717   0  1 14422 254 61   59536888
     EXT3 Large file Sparse superblock, 30 GB / 28 GiB
     Linux Swap           14423   0  1 14592 254 45    2731032
     SWAP2 version 1, 1398 MB / 1333 MiB
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8

Results
   * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
     NTFS, 26 GB / 24 GiB
   P FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
     FAT32, 61 GB / 57 GiB
   P Linux                10717   0  1 14422 254 63   59536890
     EXT3 Large file Sparse superblock, 30 GB / 28 GiB
   P Linux Swap           14423   0  1 14592 254 63    2731050
     SWAP2 version 1, 1398 MB / 1333 MiB

interface_write()
 1 * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
 2 P FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
 3 P Linux                10717   0  1 14422 254 63   59536890
 4 P Linux Swap           14423   0  1 14592 254 63    2731050
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

Analyse Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
Info: size boot_sector 52403953, partition 52403967
FAT32 at 3262/0/1
Info: size boot_sector 119764575, partition 119764575
FAT1 : 68-29300
FAT2 : 29301-58533
start_rootdir : 58566 root cluster : 3
Data : 58534-119764549
sectors : 119764575
cluster_size : 32
no_of_cluster : 3740813 (2 - 3740814)
fat_length 29233 calculated 29226
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8
Current partition structure:
 1 * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
 2 P FAT32                 3262   0  1 10716 254 63  119764575 [DATA]
 3 P Linux                10717   0  1 14422 254 63   59536890
 4 P Linux Swap           14423   0  1 14592 254 63    2731050
Backup partition structure
partition_save
Ask the user for vista mode
Allow partial last cylinder : Yes
search_vista_part: 0

search_part()
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
NTFS at 0/1/1
filesystem size           52403953
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               3276251
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1  3261 254 49   52403953 [WINDOWS]
     NTFS, 26 GB / 24 GiB
FAT32 at 3262/0/1
FAT1 : 68-29300
FAT2 : 29301-58533
start_rootdir : 58566 root cluster : 3
Data : 58534-119764549
sectors : 119764575
cluster_size : 32
no_of_cluster : 3740813 (2 - 3740814)
fat_length 29233 calculated 29226

FAT32 at 3262/0/1
     FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
     FAT32, 61 GB / 57 GiB

recover_EXT2: s_block_group_nr=0/227, s_mnt_count=19/30, s_blocks_per_group=32768, s_inodes_per_group=8176
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 7442111
recover_EXT2: part_size 59536888
     Linux                10717   0  1 14422 254 61   59536888
     EXT3 Large file Sparse superblock, 30 GB / 28 GiB
     Linux Swap           14423   0  1 14592 254 45    2731032
     SWAP2 version 1, 1398 MB / 1333 MiB
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8

Results
   * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
     NTFS, 26 GB / 24 GiB
   P FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
     FAT32, 61 GB / 57 GiB
   P Linux                10717   0  1 14422 254 63   59536890
     EXT3 Large file Sparse superblock, 30 GB / 28 GiB
   P Linux Swap           14423   0  1 14592 254 63    2731050
     SWAP2 version 1, 1398 MB / 1333 MiB

interface_write()
 1 * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
 2 P FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
 3 P Linux                10717   0  1 14422 254 63   59536890
 4 P Linux Swap           14423   0  1 14592 254 63    2731050

search_part()
Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
NTFS at 0/1/1
filesystem size           52403953
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               3276251
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1  3261 254 49   52403953 [WINDOWS]
     NTFS, 26 GB / 24 GiB
FAT32 at 3262/0/1
FAT1 : 68-29300
FAT2 : 29301-58533
start_rootdir : 58566 root cluster : 3
Data : 58534-119764549
sectors : 119764575
cluster_size : 32
no_of_cluster : 3740813 (2 - 3740814)
fat_length 29233 calculated 29226

FAT32 at 3262/0/1
     FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
     FAT32, 61 GB / 57 GiB
FAT32 at 3262/0/7
FAT1 : 68-29300
FAT2 : 29301-58533
start_rootdir : 58566 root cluster : 3
Data : 58534-119764549
sectors : 119764575
cluster_size : 32
no_of_cluster : 3740813 (2 - 3740814)
fat_length 29233 calculated 29226
set_FAT_info: name from BS used

FAT32 at 3262/0/7
     FAT32 LBA             3262   0  1 10716 254 63  119764575 [NO NAME]
     FAT found using backup sector!, 61 GB / 57 GiB

recover_EXT2: s_block_group_nr=0/227, s_mnt_count=19/30, s_blocks_per_group=32768, s_inodes_per_group=8176
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 7442111
recover_EXT2: part_size 59536888
     Linux                10717   0  1 14422 254 61   59536888
     EXT3 Large file Sparse superblock, 30 GB / 28 GiB

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/227, s_mnt_count=0/30, s_blocks_per_group=32768, s_inodes_per_group=8176
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 7442111
recover_EXT2: part_size 59536888
     Linux                10717   0  1 14422 254 61   59536888
     EXT3 Large file Sparse superblock Backup superblock, 30 GB / 28 GiB
     Linux Swap           14423   0  1 14592 254 45    2731032
     SWAP2 version 1, 1398 MB / 1333 MiB
NTFS at 14592/254/63
filesystem size           62283713
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               3892732
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          10716   4 41 14592 254 63   62283713
     NTFS found using backup sector!, 31 GB / 29 GiB
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8

Results
   * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
     NTFS, 26 GB / 24 GiB
     FAT32 LBA             3262   0  1 10716 254 63  119764575 [DATA]
     FAT32, 61 GB / 57 GiB
     HPFS - NTFS          10716   4 41 14592 254 63   62283713
     NTFS found using backup sector!, 31 GB / 29 GiB
     Linux                10717   0  1 14422 254 63   59536890
     EXT3 Large file Sparse superblock, 30 GB / 28 GiB
     Linux Swap           14423   0  1 14592 254 63    2731050
     SWAP2 version 1, 1398 MB / 1333 MiB

interface_write()
 1 * HPFS - NTFS              0   1  1  3261 254 63   52403967 [WINDOWS]
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.
ubuntu@ubuntu:~$ cat backup.log 
#1268302322 Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
 1 : start=       63, size= 52403967, Id=07, *
 2 : start= 52404030, size=119764575, Id=0B, P
 3 : start=172168605, size= 59536890, Id=83, P
 4 : start=231705495, size=  2731050, Id=82, P
#1268304491 Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
 1 : start=       63, size= 52403967, Id=07, *
 2 : start= 52404030, size=119764575, Id=0B, P
 3 : start=172168605, size= 59536890, Id=83, P
 4 : start=231705495, size=  2731050, Id=82, P
#1268304574 Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
 1 : start=       63, size= 52403967, Id=07, *
 2 : start= 52404030, size=119764575, Id=0B, P
 3 : start=172168605, size= 59536890, Id=83, P
 4 : start=231705495, size=  2731050, Id=82, P
ubuntu@ubuntu:~$ 


```

---

### Post by Intrepid Ibex on 2010-03-11
You can fill ext partitions to match the partition size with: ```
sudo resize2fs /dev/sdXX
``` and check them with: ```
sudo fsck -f /dev/sdXX
```. In either case make sure the partition isn't mounted and replace the XX'es.

---

### Post by leorolla on 2010-03-11
Thanks.

I cannot even boot from my hard disk.

It is the partition table that was corrupted or deleted.

When I boot from a live USB, standard applications cannot even recognize the HD partitions.

The problem is not with the ext3 filesystem size. I guess that after I correctly restore the partition table I will have my ext3 filesystem working fine.

---

### Post by akand074 on 2010-03-11
> **leorolla said:**
> Thanks.

I cannot even boot from my hard disk.

It is the partition table that was corrupted or deleted.

When I boot from a live USB, standard applications cannot even recognize the HD partitions.

The problem is not with the ext3 filesystem size. I guess that after I correctly restore the partition table I will have my ext3 filesystem working fine.

Yeah if you use test disk you should be able to recover all your partitions. Your ext3 partitions should boot fine, if you have a windows partition good luck getting that to boot after recovery

---

### Post by psusi on 2010-03-11
Other than the nonsense about there not being a partition table, then it prints the partition table, I don't see anything wrong there.  Have you tried to mount the partition from the liveusb and see your files?

---

### Post by srs5694 on 2010-03-11
**Step 1: Back up your current state!**

Your disk state now is clearly bad, but it could be worse. Thus, you should back it up. I recommend doing two things:


[list]
[*]Using dd, copy the MBR of each disk, as in "dd if=/dev/sda of=sda-backup.mbr bs=512 count=1", and likewise for /dev/sdb. This creates a binary copy of the primary partition table. Be sure to get the if and of options straight; if you reverse them, you'll end up wiping out your partition table!
[*]Using sfdisk, create a text-mode backup of all partitions (primary and logical), as in "sfdisk -d /dev/sda > backup-sda.txt".
[/list]


Store both backups on an external device (a network share or a USB flash drive, say). Either can be reversed should you need to recover your current (bad) partitions from an even worse state.

Once you've got the backups, you can experiment with testdisk, GNU Parted, or manual tweaking of the partition start and end points in relative safety.

Be *very* cautious with tools that might alter the filesystems, including fsck and resize2fs (or equivalent for other filesystems). In fact, I wouldn't use the latter at all, unless I was convinced that I'd found the correct start point for the partition but wasn't sure the end point was correct. When testing, mount read-only.

---

### Post by leorolla on 2010-03-11
> **akand074 said:**
> Yeah if you use test disk you should be able to recover all your partitions. Your ext3 partitions should boot fine, if you have a windows partition good luck getting that to boot after recovery

Thanks!

Don't worry, there is no Windows install.

> **psusi said:**
> Other than the nonsense about there not being a partition table, then it prints the partition table, I don't see anything wrong there.  Have you tried to mount the partition from the liveusb and see your files?

As I said,
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3ffd3ff

[B]This doesn't look like a partition table
Probably you selected the wrong device.
[/B]
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1        3262    26201983+   7  HPFS/NTFS
/dev/sda2            3263       10717    59882287+   b  W95 FAT32
/dev/sda3           10718       14423    29768445   83  Linux
/dev/sda4           14424       14593     1365525   82  Linux swap / Solaris
```And further,
```
ubuntu@ubuntu:~$ ls /dev/sd*
/dev/sda  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdb3  /dev/sdb4
ubuntu@ubuntu:~$
```(my hard disk is /dev/sda)

GParted sees a plain device, as well as Palimpsest Disk Utility.

> **srs5694 said:**
> **Step 1: Back up your current state!**

Your disk state now is clearly bad, but it could be worse. Thus, you should back it up. I recommend doing two things:


[LIST]
[*]Using dd, copy the MBR of each disk, as in "dd if=/dev/sda of=sda-backup.mbr bs=512 count=1", and likewise for /dev/sdb. This creates a binary copy of the primary partition table. Be sure to get the if and of options straight; if you reverse them, you'll end up wiping out your partition table!
[*]Using sfdisk, create a text-mode backup of all partitions (primary and logical), as in "sfdisk -d /dev/sda > backup-sda.txt".
[/LIST]


Store both backups on an external device (a network share or a USB flash drive, say). Either can be reversed should you need to recover your current (bad) partitions from an even worse state.

Once you've got the backups, you can experiment with testdisk, GNU Parted, or manual tweaking of the partition start and end points in relative safety.

Be *very* cautious with tools that might alter the filesystems, including fsck and resize2fs (or equivalent for other filesystems). In fact, I wouldn't use the latter at all, unless I was convinced that I'd found the correct start point for the partition but wasn't sure the end point was correct. When testing, mount read-only.

Thanks!

Backups made.

I will run testdisk, write the partition table, and see what happens...

---

### Post by leorolla on 2010-03-11
It worked!
Thank you for all the support and advise.
I'm posting from the recovered install.

I ran to testdisk, followed the standad procedure, and told it to write new partition table.

Everything working fine as before :-)

---

