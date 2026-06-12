---
title: "File Recovery - MyBook World Edition II  (RAID 1)"
date: 2012-04-12
forum: General Help
---

### Post by Mylorharbour on 2012-04-12
My WD Mybook World Edition II NAS died some time back. I've followed many threads trying to get access to it for management and folders but it's clearly blown.

I'm now trying to get the files off the 2TB drives. I've removed one from the NAS and connected it via USB. Here's what I've found to date:

**Gparted found 4 partitions:**
sdc1 ext3 1.87Gb
sdc2 linux-swap 251Mb
sdc3 ext3 1Gb
sdc4 unknown 1.82Tb

[B]Clearly the files are on sdc4.

In Terminal:[/B]
[I]sudo su
mkdir /mnt/world

fdisk -l[/I]
WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  3907029167  1953514583+  ee  GPT

[B]So I can't mount sdc4 as I can't find out the filesystem. That said, someone else on the forum had a very similar problem and found, using disktype, their partition was xfs. Here is their output:
[/B]
Partition 4: 1.816 TiB (1997081533440 bytes, 3900549870 sectors from 6474195)
Type 0xFD (Linux raid autodetect)
Linux RAID disk, version 0.90.0
RAID1 set using 2 regular -1 spare disks
RAID set UUID 38ECA297-F2A0-F19F-5FA2-DEAB46C142F3 (NCS)
XFS file system, version 4
Volume name ""
UUID B92F7337-EB45-44C4-82DD-38D77605D505 (DCE, v4)
Volume size 1.816 TiB (1996682428416 bytes, 487471296 blocks of 4 KiB)

[B]As it appears it should be xfs I tried to mount it:
[/B]
*sudo mount -t xfs /dev/sdc4 /mnt/world*
mount: wrong fs type, bad option, bad superblock on /dev/sdc4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

**So I ran disktype on my sdc:**
[I]
sudo disktype /dev/sdc[/I]

--- /dev/sdc
Block device, size 1.819 TiB (2000398934016 bytes)
DOS/MBR partition map
Partition 1: 1.819 TiB (2000398933504 bytes, 3907029167 sectors from 1)
  Type 0xEE (EFI GPT protective)
GPT partition map, 128 entries
  Disk size 1.819 TiB (2000398934016 bytes, 3907029168 sectors)
  Disk GUID 0F27E779-2C6A-3D48-993D-B0E0EF109647
Partition 1: 1.869 GiB (2006974464 bytes, 3919872 sectors from 64320)
  Type Linux RAID (GUID 0F889DA1-FC05-3B4D-A006-743F0F84911E)
  Partition Name "primary"
  Partition GUID E38011AA-3C53-B940-9953-AA51EBD12EF5
  Ext3 file system
    UUID A43B0BE4-F843-4901-8BE2-85737439D5E8 (DCE, v4)
    Volume size 1.869 GiB (2006908928 bytes, 489968 blocks of 4 KiB)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular 0 spare disks
    RAID set UUID AF760207-74A2-A5B4-64EE-1BF90A2CC44C (NCS)
Partition 2: 251.0 MiB (263159808 bytes, 513984 sectors from 3984192)
  Type Linux RAID (GUID 0F889DA1-FC05-3B4D-A006-743F0F84911E)
  Partition Name "primary"
  Partition GUID 8C8E0D09-F315-EA4B-9FC7-A25D9CB8DEEA
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular 0 spare disks
    RAID set UUID 78C8DF6C-74AB-3BF1-64EE-1BF90A2CC44C (NCS)
  Linux swap, version 2, subversion 1, 4 KiB pages, little-endian
    Swap size 250.9 MiB (263053312 bytes, 64222 pages of 4 KiB)
Partition 3: 964.8 MiB (1011712000 bytes, 1976000 sectors from 4498176)
  Type Linux RAID (GUID 0F889DA1-FC05-3B4D-A006-743F0F84911E)
  Partition Name "primary"
  Partition GUID BBB00E4E-42C4-324B-81A2-A8DA6B2CCB5F
  Ext3 file system
    UUID 5B3C3670-D3C8-4994-8187-44AA564C7EF2 (DCE, v4)
    Volume size 964.8 MiB (1011613696 bytes, 246976 blocks of 4 KiB)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular 0 spare disks
    RAID set UUID 07085D07-B76B-494C-64EE-1BF90A2CC44C (NCS)
Partition 4: 1.816 TiB (1997084139008 bytes, 3900554959 sectors from 6474176)
  Type Linux RAID (GUID 0F889DA1-FC05-3B4D-A006-743F0F84911E)
  Partition Name "primary"
  Partition GUID B4C60A08-D1E1-134D-9030-AD0C58B6E56C
Partition 5: unused

**Partition 5?? This looks like truly bad news. What do you guys think?**

---

### Post by leecook on 2012-08-05
I am trying to solve this problem for myself right now - did you find the solution?

---

