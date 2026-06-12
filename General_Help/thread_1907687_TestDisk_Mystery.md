---
title: "TestDisk Mystery"
date: 2012-01-11
forum: General Help
---

### Post by BaconLT on 2012-01-11
As a preface, simply following the TestDisk tutorials and scouring the forums let me nowhere. I found a lot of solutions to a lot of problems, but none that seem to resemble mine exactly enough for me to solve them.

I have a corrupted partition table on a 32G USB thumb drive. Fdisk shows this: 

[FONT="Fixedsys"]Disk /dev/sdd: 31.8 GB, 31750881280 bytes
64 heads, 32 sectors/track, 30280 cylinders, total 62013440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x23a567f5

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?  1184891080  2320662151   567885536    d  Unknown
/dev/sdd2        69240904    69240969          33    4  FAT16 <32M
/dev/sdd3      2147944456  2152155935     2105740   10  OPUS
/dev/sdd4   ?   269091841  2419214368  1075061264   6a  Unknown

Partition table entries are not in disk order

[/FONT]

The disk WAS one partition - I think FAT32.

I used TestDisk to try to recover the structure. Initially, this is what I get: 
[FONT="Fixedsys"]Disk /dev/sdd - 31 GB / 29 GiB - CHS 30280 64 32
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Sys=0D               578560   6  9 1133135  52  8 1135771072

Warning: Bad ending sector (CHS and LBA don't match)
check_FAT: can't read FAT boot sector
Invalid FAT boot sector
 2 P FAT16 <32M           33809   2  9 33809   4 10         66
 2 P FAT16 <32M           33809   2  9 33809   4 10         66

Warning: Bad starting sector (CHS and LBA don't match)
 3 P OPUS                 1048801   0  9 1050857  24 32    4211480

Warning: Bad starting sector (CHS and LBA don't match)
 4 * Sys=6A               131392  32  2 1181257   1  1 2150122528

Warning: Bad ending sector (CHS and LBA don't match)
Only one partition must be bootable
Space conflict between the following two partitions
 4 * Sys=6A               131392  32  2 1181257   1  1 2150122528
 1 * Sys=0D               578560   6  9 1133135  52  8 1135771072
Space conflict between the following two partitions
 1 * Sys=0D               578560   6  9 1133135  52  8 1135771072
 3 P OPUS                 1048801   0  9 1050857  24 32    4211480
[/FONT]

Then after Quicksearch: 

[FONT="Fixedsys"]Disk /dev/sdd - 31 GB / 29 GiB - CHS 30280 64 32

Warning: the current number of heads per cylinder is 64
but the correct value may be 255.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.

[/FONT]

And after Continue: 

[FONT="Fixedsys"]Disk /dev/sdd - 31 GB / 29 GiB - CHS 30280 64 32
     Partition               Start        End    Size in sectors
>* FAT32 LBA                0   1  1 30279  63 32   62013408 [DISK_IMG]
[/FONT]

When I tap 'p', the ugly truth confronts me:
[FONT="Fixedsys"]   * FAT32 LBA                0   1  1 30279  63 32   62013408 [DISK_IMG]
Directory /

>-r-xr-xr-x     0     0 685011246 27-Jul-2003 03:09 Yd&#65533;]&#65533;c]b
 drwxr-xr-x     0     0 3152325290 24-Dec-1934 03:42 ^_Q~Q~B_QZY.V>Y
 drwxr-xr-x     0     0 375828354 10-May-2000 21:23 &#65533;h&#65533;&#65533;&#1634;&#65533;[.&#65533;&#65533;S
 -rwxr-xr-x     0     0 1478710608  3-Jan-2019 11:00 &#65533;e&#65533;&#65533;&#65533;O&#65533;7.v&#891;
[/FONT]

and many, MANY, more corrupted file names.

PhotoRec recovered all of the files, so at least I have the thousand or so photos that were there, but there are a lot of important executables and directories on this drive. 

Is it a lost cause at this point or is the directory structure recoverable?

---

### Post by BaconLT on 2012-01-12
Workaround - I got in to work today and there is a backup. Thank heaven.

---

### Post by alphaamanitin on 2012-01-12
Don't know if I would trust that USB drive if I were you.  

alphaA

---

