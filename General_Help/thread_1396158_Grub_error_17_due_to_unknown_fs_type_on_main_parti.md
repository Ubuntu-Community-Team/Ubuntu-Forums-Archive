---
title: "Grub error 17 due to unknown fs type on main partition"
date: 2010-02-01
forum: General Help
---

### Post by jamesisin on 2010-02-01
A formerly working system now gives an 'error 17' at Grub instead of booting.

Here are the facts I have gathered thus far.

$ blkid

n/a (no output)

$ sudo fdisk -l /dev/sda

```
Disk /dev/sda: 60.1 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb639

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7115    57151206   83  Linux
/dev/sda2            7116        7301     1494045    5  Extended
/dev/sda5            7116        7301     1494013+  82  Linux swap / Solaris
```

$ sudo parted /dev/sda print

```
Model: ATA SAMSUNG SV6003H (scsi)
Disk /dev/sda: 60.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  58.5GB  58.5GB  primary                   boot
 2      58.5GB  60.1GB  1530MB  extended
 5      58.5GB  60.1GB  1530MB  logical   linux-swap(v1)
```

$ sudo mount -t ext3 /dev/sda1 /media/sda1
or
$ sudo mount -t ext4 /dev/sda2 /media/sda1

```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

$ dmesg | tail

```
[ 1504.265150] VFS: Can't find ext3 filesystem on dev sda1.
...
[ 3573.902979] attempt to access beyond end of device
[ 3573.902995] sda2: rw=0, want=4, limit=2
[ 3573.903004] EXT3-fs: unable to read superblock
[ 6331.278800] attempt to access beyond end of device
[ 6331.278815] sda2: rw=0, want=4, limit=2
[ 6331.278825] EXT4-fs (sda2): unable to read superblock
```

GParted lists the file system as 'unknown' and palimpsest calls it 'unrecognized, unused, or unknown'.

The machine is running 9.04 desktop.

Where do we go from here?

---

### Post by Leppie on 2010-02-01
try accessing the partition with fdisk:
```
sudo fdisk /dev/sda1
```
if it prompts you to it can correct some errors on the partition, have it do it, you can then check the filesystem for errors with fsck.

---

### Post by jamesisin on 2010-02-01
Leppie - Thanks.  I don't know how to use fdisk well.  When I run the command you recommend I am left with a special command prompt (for fdisk).  I was not prompted in any way.  Can you recommend a super-sweet fdisk command?  I tried w but that seems to have done nothing.

```
$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 7301.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): v
14551 unallocated 512-byte sectors
```

(In case it matters, the live CD I am using is 9.10.)

---

### Post by jamesisin on 2010-02-01
Sorry, I think the file system is actually ext4 (but this doesn't change much from above).

Here is some more useful output (and I will correct the first post).

$ sudo mount -t ext4 /dev/sda2 /media/sda1

```
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

$ dmesg | tail

```
[ 3573.902979] attempt to access beyond end of device
[ 3573.902995] sda2: rw=0, want=4, limit=2
[ 3573.903004] EXT3-fs: unable to read superblock
[ 6331.278800] attempt to access beyond end of device
[ 6331.278815] sda2: rw=0, want=4, limit=2
[ 6331.278825] EXT4-fs (sda2): unable to read superblock
```

---

### Post by Leppie on 2010-02-01
well, often fdisk picks up minor issues with partition tables. however, it doesn't seem to have worked for you. so unfortunately no super sweet fdisk command here to solve this issue. the w command writes to disk, this is to commit changes (hopefully you didn't change anything there ;)).
have you ever tried testdisk? it can restore your partition table without touching the actual data in the partition.
```
sudo apt-get install testdisk
sudo testdisk
```there's some information here: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

if the normal scan doesn't find the correct partition type, go for the deep scan (though this may take quite a while)

---

### Post by jamesisin on 2010-02-01
I have heard of it.  I looked for it in synaptic and didn't see it.

```
$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
```

No love.

---

### Post by Leppie on 2010-02-01
sorry, i should've told you to enable the "universe" repository first.
System>Administration>Software Sources>Ubuntu Software.

---

### Post by jamesisin on 2010-02-01
Doh, I made the same mistake.

Got that settled.

I have now run testdisk twice.  The first time I did the deep scan (the regular scan only finds the extended and swap partitions) and instructed it to write the partition information to the disk.  This, it said, required a reboot.

Nothing changed.

I ran it again and did the same as above but also instructed it to write the table.

Nothing of use has changed.

I do now get the 1234F: prompt at boot time.  All of the possible choices except 2 do nothing (returns the prompt).  Using 2 just hangs the prompt.

I have now pulled that drive and it is in a USB tray attached to my 8.10 machine.  I am running through testdisk again, but I have little hope that it will offer any different results.

Still seeking help to sort out this drive/filesystem problem.

---

### Post by jamesisin on 2010-02-01
USB attached gave the same results (reboot?  why?).

---

### Post by jamesisin on 2010-02-02
Opening Analyze shows this:

```
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

No EXT2, JFS, Reiser, cramfs or XFS marker
 1 * Linux                    0   1  1  7114 254 63  114302412
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
```

After running Quick Search I get this:

```
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63

     Partition                  Start        End    Size in sectors

 1 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
```

After the Deeper Search I get this:

```
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63

     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
```

At which point I choose Write (and am told a reboot is required).

Having run this twice (on this machine) and having set the log to append, here is that appended log showing both runs (we are only concerned with sdd):

```
Mon Feb  1 19:13:33 2010
Command line: TestDisk

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Linux version (ext2fs lib: 1.41.3, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none)
Hard disk list
Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63, sector size=512 - ATA WDC WD800JB-00CR
Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512 - ATA ST3160021A
Disk /dev/sdc - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA WDC WD5000AAKB-0
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63, sector size=512 - SAMSUNG SV6003H

Disk /dev/sdd - 60 GB / 55 GiB - SAMSUNG SV6003H
Partition table type: Intel

Analyse Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 83
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6
Current partition structure:
No EXT2, JFS, Reiser, cramfs or XFS marker
 1 * Linux                    0   1  1  7114 254 63  114302412
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63
   D Linux Swap            7115   1  1  7300 254 44    2988008
     SWAP2 version 1, 1529 MB / 1458 MiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=255 nbr=2

Results
   L Linux Swap            7115   1  1  7300 254 63    2988027
     SWAP2 version 1, 1529 MB / 1458 MiB

interface_write()
 1 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027

search_part()
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
   D Linux                    0   1  1  7114 254 59  114302408
     EXT3 Large file Sparse superblock Backup superblock, 58 GB / 54 GiB
   D Linux Swap            7115   1  1  7300 254 44    2988008
     SWAP2 version 1, 1529 MB / 1458 MiB
get_geometry_from_list_part_aux head=255 nbr=4
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=4

Results
   * Linux                    0   1  1  7114 254 63  114302412
     EXT3 Large file Sparse superblock Backup superblock, 58 GB / 54 GiB
   L Linux Swap            7115   1  1  7300 254 63    2988027
     SWAP2 version 1, 1529 MB / 1458 MiB

interface_write()
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
write!

write_mbr_i386: starting...
write_all_log_i386: starting...
write_all_log_i386: CHS: 7115/0/1,lba=114302475
Need to fix
 1 * Linux                    0   1  1  7114 254 63  114302412
     EXT3 Large file Sparse superblock Backup superblock, 58 GB / 54 GiB
You will have to reboot for the change to take effect.

Interface Advanced
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 83
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
     SWAP2 version 1, 1529 MB / 1458 MiB
search_superblock

block_group_nr 1

recover_EXT2: "e2fsck -b 32768 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=1/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 262144 (block=32768, blocksize=4096)

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 786432 (block=98304, blocksize=4096)

block_group_nr 5

recover_EXT2: "e2fsck -b 163840 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=5/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 1310720 (block=163840, blocksize=4096)

block_group_nr 7

recover_EXT2: "e2fsck -b 229376 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=7/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 1835008 (block=229376, blocksize=4096)

block_group_nr 9

recover_EXT2: "e2fsck -b 294912 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=9/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 2359296 (block=294912, blocksize=4096)

block_group_nr 25

recover_EXT2: "e2fsck -b 819200 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=25/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 6553600 (block=819200, blocksize=4096)

block_group_nr 27

recover_EXT2: "e2fsck -b 884736 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=27/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 7077888 (block=884736, blocksize=4096)

block_group_nr 49

recover_EXT2: "e2fsck -b 1605632 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=49/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 12845056 (block=1605632, blocksize=4096)

block_group_nr 81

recover_EXT2: "e2fsck -b 2654208 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=81/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 21233664 (block=2654208, blocksize=4096)

block_group_nr 125

recover_EXT2: "e2fsck -b 4096000 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=125/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 32768000 (block=4096000, blocksize=4096)
  Linux                    0   1  1  7114 254 59  114302408
superblock 32768, blocksize=4096
superblock 98304, blocksize=4096
superblock 163840, blocksize=4096
superblock 229376, blocksize=4096
superblock 294912, blocksize=4096
superblock 819200, blocksize=4096
superblock 884736, blocksize=4096
superblock 1605632, blocksize=4096
superblock 2654208, blocksize=4096
superblock 4096000, blocksize=4096
A new copy of MBR code has been written.
You have to reboot for the change to take effect.

TestDisk exited normally.


Mon Feb  1 20:40:26 2010
Command line: TestDisk

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Linux version (ext2fs lib: 1.41.3, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none)
Hard disk list
Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63, sector size=512 - ATA WDC WD800JB-00CR
Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512 - ATA ST3160021A
Disk /dev/sdc - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA WDC WD5000AAKB-0
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63, sector size=512 - SAMSUNG SV6003H

Disk /dev/sdd - 60 GB / 55 GiB - SAMSUNG SV6003H
Partition table type: Intel

Analyse Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 83
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6
Current partition structure:
No EXT2, JFS, Reiser, cramfs or XFS marker
 1 * Linux                    0   1  1  7114 254 63  114302412
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63
   D Linux Swap            7115   1  1  7300 254 44    2988008
     SWAP2 version 1, 1529 MB / 1458 MiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=255 nbr=2

Results
   L Linux Swap            7115   1  1  7300 254 63    2988027
     SWAP2 version 1, 1529 MB / 1458 MiB

interface_write()
 1 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027

search_part()
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
   D Linux                    0   1  1  7114 254 59  114302408
     EXT3 Large file Sparse superblock Backup superblock, 58 GB / 54 GiB
   D Linux Swap            7115   1  1  7300 254 44    2988008
     SWAP2 version 1, 1529 MB / 1458 MiB
get_geometry_from_list_part_aux head=255 nbr=4
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=4

Results
   * Linux                    0   1  1  7114 254 63  114302412
     EXT3 Large file Sparse superblock Backup superblock, 58 GB / 54 GiB
   L Linux Swap            7115   1  1  7300 254 63    2988027
     SWAP2 version 1, 1529 MB / 1458 MiB

interface_write()
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
```

As you can see the screen output and the log are consistent.

Can someone help with any next steps?  I am getting nowhere or so it seems.

---

### Post by Dalek Draco ON LINUX on 2010-02-02
[http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/)  The above link should provide an easy solution (it looked easy to me).  The last time I had a grub error I reinstalled the OS because I couldn't work out how to fix it (no boot, came up grub error something or other).  Hope that helps.

---

### Post by jamesisin on 2010-02-02
Thanks.  That solution hinges upon the partition order being incorrect (where mine is correct).  I did leave a comment for the blogger in hopes that will encourage said blogger's participation on this thread.

---

### Post by jamesisin on 2010-02-02
I tried to use testdisk to create an image from which I might pull files.  It created a file called image.dd (~55GB) on which I tried to run fdisk:

```
$ fdisk -u -l /media/Musica/image.dd 

Disk /media/Musica/image.dd: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c69616d

Disk /media/Musica/image.dd doesn't contain a valid partition table
```

I can't figure out how I might otherwise use this image file.

---

### Post by Leppie on 2010-02-02
> **jamesisin said:**
> As you can see the screen output and the log are consistent.

Can someone help with any next steps?  I am getting nowhere or so it seems.
after the testdisk operations, have you been able to access the partition from your other machine (8.10)?

---

### Post by Leppie on 2010-02-02
[removed]

---

### Post by red eye dragon on 2010-02-02
ok going to try and keep it simple
> **jamesisin said:**
> Opening Analyze shows this:

```
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

No EXT2, JFS, Reiser, cramfs or XFS marker
 1 * Linux                    0   1  1  7114 254 63  114302412
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
```After running Quick Search I get this:

```
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63

     Partition                  Start        End    Size in sectors

 1 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
```After the Deeper Search I get this:

```
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63

     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
```At which point I choose Write (and am told a reboot is required).

Having run this twice (on this machine) and having set the log to append, here is that appended log showing both runs (we are only concerned with sdd):

```
Mon Feb  1 19:13:33 2010
Command line: TestDisk

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Linux version (ext2fs lib: 1.41.3, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none)
Hard disk list
Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63, sector size=512 - ATA WDC WD800JB-00CR
Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512 - ATA ST3160021A
Disk /dev/sdc - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA WDC WD5000AAKB-0
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63, sector size=512 - SAMSUNG SV6003H

Disk /dev/sdd - 60 GB / 55 GiB - SAMSUNG SV6003H
Partition table type: Intel

Analyse Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 83
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6
Current partition structure:
No EXT2, JFS, Reiser, cramfs or XFS marker
 1 * Linux                    0   1  1  7114 254 63  114302412
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63
   D Linux Swap            7115   1  1  7300 254 44    2988008
     SWAP2 version 1, 1529 MB / 1458 MiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=255 nbr=2

Results
   L Linux Swap            7115   1  1  7300 254 63    2988027
     SWAP2 version 1, 1529 MB / 1458 MiB

interface_write()
 1 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027

search_part()
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
   D Linux                    0   1  1  7114 254 59  114302408
     EXT3 Large file Sparse superblock Backup superblock, 58 GB / 54 GiB
   D Linux Swap            7115   1  1  7300 254 44    2988008
     SWAP2 version 1, 1529 MB / 1458 MiB
get_geometry_from_list_part_aux head=255 nbr=4
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=4

Results
   * Linux                    0   1  1  7114 254 63  114302412
     EXT3 Large file Sparse superblock Backup superblock, 58 GB / 54 GiB
   L Linux Swap            7115   1  1  7300 254 63    2988027
     SWAP2 version 1, 1529 MB / 1458 MiB

interface_write()
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
write!

write_mbr_i386: starting...
write_all_log_i386: starting...
write_all_log_i386: CHS: 7115/0/1,lba=114302475
Need to fix
 1 * Linux                    0   1  1  7114 254 63  114302412
     EXT3 Large file Sparse superblock Backup superblock, 58 GB / 54 GiB
You will have to reboot for the change to take effect.

Interface Advanced
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 83
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
     SWAP2 version 1, 1529 MB / 1458 MiB
search_superblock

block_group_nr 1

recover_EXT2: "e2fsck -b 32768 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=1/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 262144 (block=32768, blocksize=4096)

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 786432 (block=98304, blocksize=4096)

block_group_nr 5

recover_EXT2: "e2fsck -b 163840 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=5/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 1310720 (block=163840, blocksize=4096)

block_group_nr 7

recover_EXT2: "e2fsck -b 229376 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=7/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 1835008 (block=229376, blocksize=4096)

block_group_nr 9

recover_EXT2: "e2fsck -b 294912 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=9/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 2359296 (block=294912, blocksize=4096)

block_group_nr 25

recover_EXT2: "e2fsck -b 819200 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=25/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 6553600 (block=819200, blocksize=4096)

block_group_nr 27

recover_EXT2: "e2fsck -b 884736 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=27/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 7077888 (block=884736, blocksize=4096)

block_group_nr 49

recover_EXT2: "e2fsck -b 1605632 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=49/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 12845056 (block=1605632, blocksize=4096)

block_group_nr 81

recover_EXT2: "e2fsck -b 2654208 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=81/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 21233664 (block=2654208, blocksize=4096)

block_group_nr 125

recover_EXT2: "e2fsck -b 4096000 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=125/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
Ext2 superblock found at sector 32768000 (block=4096000, blocksize=4096)
  Linux                    0   1  1  7114 254 59  114302408
superblock 32768, blocksize=4096
superblock 98304, blocksize=4096
superblock 163840, blocksize=4096
superblock 229376, blocksize=4096
superblock 294912, blocksize=4096
superblock 819200, blocksize=4096
superblock 884736, blocksize=4096
superblock 1605632, blocksize=4096
superblock 2654208, blocksize=4096
superblock 4096000, blocksize=4096
A new copy of MBR code has been written.
You have to reboot for the change to take effect.

TestDisk exited normally.


Mon Feb  1 20:40:26 2010
Command line: TestDisk

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Linux version (ext2fs lib: 1.41.3, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none)
Hard disk list
Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63, sector size=512 - ATA WDC WD800JB-00CR
Disk /dev/sdb - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512 - ATA ST3160021A
Disk /dev/sdc - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA WDC WD5000AAKB-0
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63, sector size=512 - SAMSUNG SV6003H

Disk /dev/sdd - 60 GB / 55 GiB - SAMSUNG SV6003H
Partition table type: Intel

Analyse Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 83
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=6
Current partition structure:
No EXT2, JFS, Reiser, cramfs or XFS marker
 1 * Linux                    0   1  1  7114 254 63  114302412
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63
   D Linux Swap            7115   1  1  7300 254 44    2988008
     SWAP2 version 1, 1529 MB / 1458 MiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=255 nbr=2

Results
   L Linux Swap            7115   1  1  7300 254 63    2988027
     SWAP2 version 1, 1529 MB / 1458 MiB

interface_write()
 1 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027

search_part()
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/436, s_mnt_count=0/29, s_blocks_per_group=32768
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 14287801
recover_EXT2: part_size 114302408
   D Linux                    0   1  1  7114 254 59  114302408
     EXT3 Large file Sparse superblock Backup superblock, 58 GB / 54 GiB
   D Linux Swap            7115   1  1  7300 254 44    2988008
     SWAP2 version 1, 1529 MB / 1458 MiB
get_geometry_from_list_part_aux head=255 nbr=4
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=4

Results
   * Linux                    0   1  1  7114 254 63  114302412
     EXT3 Large file Sparse superblock Backup superblock, 58 GB / 54 GiB
   L Linux Swap            7115   1  1  7300 254 63    2988027
     SWAP2 version 1, 1529 MB / 1458 MiB

interface_write()
 1 * Linux                    0   1  1  7114 254 63  114302412
 2 E extended LBA          7115   0  1  7300 254 63    2988090
 5 L Linux Swap            7115   1  1  7300 254 63    2988027
```As you can see the screen output and the log are consistent.

Can someone help with any next steps?  I am getting nowhere or so it seems.

---

### Post by jamesisin on 2010-02-02
> **Leppie said:**
> after the testdisk operations, have you been able to access the partition from your other machine (8.10)?

Mount attempts remain the same (well, 8.10 doesn't know ext4 but using ext3 should work).

> **red eye dragon said:**
> ok going to try and keep it simple

You quoted my large post but made no other comment.

---

### Post by jamesisin on 2010-02-02
In case this is useful to anyone, here is the superblock output from testdisk:

```
Disk /dev/sdd - 60 GB / 55 GiB - CHS 7301 255 63

     Partition                  Start        End    Size in sectors

  Linux                    0   1  1  7114 254 59  114302408
superblock 32768, blocksize=4096
superblock 98304, blocksize=4096
superblock 163840, blocksize=4096
superblock 229376, blocksize=4096
superblock 294912, blocksize=4096
superblock 819200, blocksize=4096
superblock 884736, blocksize=4096
superblock 1605632, blocksize=4096
superblock 2654208, blocksize=4096
superblock 4096000, blocksize=4096
```

---

### Post by Leppie on 2010-02-02
> **jamesisin said:**
> Mount attempts remain the same (well, 8.10 doesn't know ext4 but using ext3 should work).
so you have been able yo save as ext4 using testdisk?
there's several options in testdisk, one of them is to modify the partition table. did you try this?

---

### Post by jamesisin on 2010-02-02
> **Leppie said:**
> so you have been able yo save as ext4 using testdisk?
there's several options in testdisk, one of them is to modify the partition table. did you try this?

Can you be more specific?

After running Deeper I did instruct it to save (which then required a supposed reboot).  I have done that a few times.  The applications able to read the table before are able to after, and those not able to before are still not able.

Testdisk doesn't appear to distinguish between ext3 and ext4 in that it doesn't tell me which the Linux partition is:

```
1 * Linux                    0   1  1  7114 254 63  114302412
```

---

### Post by Leppie on 2010-02-02
you can try to force another check using another superblock:
```
sudo fsck.ext4 -pf -b 1605632 -B 4096 /dev/sda2
```

try some of the other superblocks from the testdisk output you posted as well if this one doesn't work either.

---

### Post by jamesisin on 2010-02-02
Here is what I get:

```
$ sudo fsck.ext4 -pf -b 1605632 -B 4096 /dev/sdd1
/dev/sdd1: Inode 228961 is in use, but has dtime set.  FIXED.
/dev/sdd1: Inode 228961 has imagic flag set.  

/dev/sdd1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
```

Next?

(Also, should I run that on all three partitions or just 1?)

---

### Post by Leppie on 2010-02-02
> **jamesisin said:**
> Here is what I get:

```
$ sudo fsck.ext4 -pf -b 1605632 -B 4096 /dev/sdd1
/dev/sdd1: Inode 228961 is in use, but has dtime set.  FIXED.
/dev/sdd1: Inode 228961 has imagic flag set.  

/dev/sdd1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
```Next?

(Also, should I run that on all three partitions or just 1?)


try this one:
```
sudo fsck.ext4 -pf -b 98304  -B 4096 /dev/sdd1
```

you showed a couple of posts with reference to sda2 so i presumed it was that one, but then i re-read and saw it was actually sda1. sorry about that, good thing you're still awake and not blindly following ;)

---

### Post by jamesisin on 2010-02-02
Yeah, the first output was from running in the other machine off the CD.  Now I have that drive in my main machine coming over USB.  Same but different.

```
$ sudo fsck.ext4 -pf -b 98304  -B 4096 /dev/sdd1 
/dev/sdd1: Inode 228961 has imagic flag set.  

/dev/sdd1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
```

---

### Post by Leppie on 2010-02-02
> **jamesisin said:**
> ```
$ sudo fsck.ext4 -pf -b 98304  -B 4096 /dev/sdd1 
/dev/sdd1: Inode 228961 has imagic flag set.  

/dev/sdd1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
```
try the command without the p option:
```
sudo fsck.ext4 -f -b 98304  -B 4096 /dev/sdd1 
```

---

### Post by jamesisin on 2010-02-02
Yassir:

```
$ sudo fsck.ext4 -f -b 98304  -B 4096 /dev/sdd1
e2fsck 1.41.3 (12-Oct-2008)
Pass 1: Checking inodes, blocks, and sizes
Inode 228961 has imagic flag set.  Clear<y>?
```

Y?

(iMagic?  Steve Jobs playing basketball?)

---

### Post by Leppie on 2010-02-02
yes, clear the bugger ;)

---

### Post by jamesisin on 2010-02-02
Is there a "yes to all"?

```
Inode 228961 has imagic flag set.  Clear<y>? yes

Inode 228961 has a extra size (26670) which is invalid
Fix<y>? yes

Inode 228962 has EXTENTS_FL flag set on filesystem without extents support.
Clear<y>? yes

Inode 228963 is in use, but has dtime set.  Fix<y>? yes

Inode 228963 has imagic flag set.  Clear<y>? yes

Inode 228963 has a extra size (29487) which is invalid
Fix<y>? yes

Inode 228964 is in use, but has dtime set.  Fix<y>? yes

Inode 228964 has imagic flag set.  Clear<y>? yes

Inode 228964 has a extra size (28530) which is invalid
Fix<y>? yes
```

---

### Post by jamesisin on 2010-02-03
I did a little reading and with 9.04 ext3 was still the default file system (though ext4 was available).  I suspect that I would have used the default when I built this machine.  So maybe we should be looking at fixing ext3.  Is there really no way to determine which file system we are seeing here (83 Linux tells too little)?

---

### Post by Leppie on 2010-02-03
> **jamesisin said:**
> Is there a "yes to all"?

```
Inode 228961 has imagic flag set.  Clear<y>? yes

Inode 228961 has a extra size (26670) which is invalid
Fix<y>? yes

Inode 228962 has EXTENTS_FL flag set on filesystem without extents support.
Clear<y>? yes

Inode 228963 is in use, but has dtime set.  Fix<y>? yes

Inode 228963 has imagic flag set.  Clear<y>? yes

Inode 228963 has a extra size (29487) which is invalid
Fix<y>? yes

Inode 228964 is in use, but has dtime set.  Fix<y>? yes

Inode 228964 has imagic flag set.  Clear<y>? yes

Inode 228964 has a extra size (28530) which is invalid
Fix<y>? yes
```
the "yes to all" option was the "p" switch which was not allowed.

---

### Post by Leppie on 2010-02-03
> **jamesisin said:**
> I did a little reading and with 9.04 ext3 was still the default file system (though ext4 was available).  I suspect that I would have used the default when I built this machine.  So maybe we should be looking at fixing ext3.  Is there really no way to determine which file system we are seeing here (83 Linux tells too little)?
then try the following:
```
sudo fsck.ext3 -pf -b 98304  -B 4096 /dev/sdd1
```if it prompts you to run manually again, issue the same command but without the "p" switch.

alternatively try without specifying the filesystem:
```
sudo fsck -pf -b 98304  -B 4096 /dev/sdd1
```

---

### Post by jamesisin on 2010-02-03
I was able to eventually get through the whole drive.

```
sudo fsck.ext3 -pf -b 98304  -B 4096 /dev/sdd1
```

It took ***FOREVER***.  I found myself just holding down the Y key for a stretch and hoping for the best.

On the positive side, I have now mounted the drive and am copying the /home folder onto a backup location.  Once that finishes I will put the drive back into its machine and see if it will boot properly.

I am inclined not to trust this build/drive.  Thoughts?

---

### Post by jamesisin on 2010-02-03
Grrr.  I am still getting this MBR 1234F: prompt at boot time.  How can I ditch that and get back to grub?

---

### Post by Leppie on 2010-02-04
booting off the livecd, issue the following commands to reinstall grub to the mbr:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by jamesisin on 2010-02-11
That did something.  Now I boot into a grub prompt.

---

### Post by Leppie on 2010-02-11
what output does the "set" (without the quotes) command produce?

---

### Post by jamesisin on 2010-02-11
Most fields are empty.  Except these two:

```
prefix=(hd0,1)/boot/grub
root=hd0,1
```

---

### Post by Leppie on 2010-02-12
then boot like this:
```
set root=(hd0,1)
insmod ext2
insmod linux
linux /vmlinuz root=/dev/sda1 ro
intrd /initrd.img
boot
```
once logged in, regenerate your grub.cfg:
```
sudo update-grub
```

---

### Post by jamesisin on 2010-02-12
I was able to boot into the system using the grub commands you recommended.  I then ran the update for grub.  However, I am still confronted with a grub prompt at boot time.  Something we missed?

---

