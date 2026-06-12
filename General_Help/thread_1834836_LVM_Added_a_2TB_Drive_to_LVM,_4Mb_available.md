---
title: "LVM: Added a 2TB Drive to LVM, 4Mb available"
date: 2011-08-28
forum: General Help
---

### Post by jgrimmster on 2011-08-28
So I added an additional 2Tb drive to my LVM and I can't seem to get the extra space to be usable. Webmin shows that the drive has been added to the LV but the system isn't recognizing it. Output below seems to indicate that the drive is full, ??

jason@server:~$ sudo lvdisplay
--- Logical volume ---
LV Name /dev/server/server
VG Name server
LV UUID yS65HN-jeIs-gMgQ-Ngb3-jyYV-RUFh-iAvPB3
LV Write Access read/write
LV Status available
# open 1
LV Size 7.28 TiB
Current LE 1907724
Segments 4
Allocation inherit
Read ahead sectors auto
- currently set to 256
Block device 252:0

jason@server:~$ sudo vgdisplay
--- Volume group ---
VG Name server
System ID
Format lvm2
Metadata Areas 4
Metadata Sequence No 23
VG Access read/write
VG Status resizable
MAX LV 0
Cur LV 1
Open LV 1
Max PV 0
Cur PV 4
Act PV 4
VG Size 7.28 TiB
PE Size 4.00 MiB
Total PE 1907724
Alloc PE / Size 1907724 / 7.28 TiB
Free PE / Size 0 / 0
VG UUID oOpv1B-oP12-wc2b-yWOH-781a-63EF-5CV1UO

jason@server:~$ sudo pvdisplay
--- Physical volume ---
PV Name /dev/sdb1
VG Name server
PV Size 1.82 TiB / not usable 2.56 MiB
Allocatable yes (but full)
PE Size 4.00 MiB
Total PE 476931
Free PE 0
Allocated PE 476931
PV UUID gqYqMJ-YFTv-i4EB-nbc1-vwUv-ZSCR-xsBqEo

--- Physical volume ---
PV Name /dev/sdc1
VG Name server
PV Size 1.82 TiB / not usable 2.56 MiB
Allocatable yes (but full)
PE Size 4.00 MiB
Total PE 476931
Free PE 0
Allocated PE 476931
PV UUID lzU826-A05x-ENRu-yPMZ-Zym9-hibd-3GwLUt

--- Physical volume ---
PV Name /dev/sdd1
VG Name server
PV Size 1.82 TiB / not usable 2.56 MiB
Allocatable yes (but full)
PE Size 4.00 MiB
Total PE 476931
Free PE 0
Allocated PE 476931
PV UUID 4P3BWA-tpwx-fVQc-oHi8-xPXR-uO9Z-WpOFWy

--- Physical volume ---
PV Name /dev/sde1
VG Name server
PV Size 1.82 TiB / not usable 2.38 MiB
Allocatable yes (but full)
PE Size 4.00 MiB
Total PE 476931
Free PE 0
Allocated PE 476931
PV UUID 2wsj2m-Asa9-oLPf-edt1-eqHc-9Xu2-ri54M3

jason@server:~$

jason@server:~$ sudo fdisk -l

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x63de5663

Device Boot Start End Blocks Id System
/dev/sdb1 1 243201 1953512001 8e Linux LVM

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007f8e5

Device Boot Start End Blocks Id System
/dev/sda1 * 1 18963 152316928 83 Linux
/dev/sda2 18963 19453 3930113 5 Extended
/dev/sda5 18963 19453 3930112 82 Linux swap / Solaris

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x66af854c

Device Boot Start End Blocks Id System
/dev/sdc1 1 243201 1953512001 8e Linux LVM

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe63cb079

Device Boot Start End Blocks Id System
/dev/sdd1 1 243201 1953512001 8e Linux LVM

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00033c0d

Device Boot Start End Blocks Id System
/dev/sde1 1 243201 1953512001 8e Linux LVM

Disk /dev/dm-0: 8001.6 GB, 8001574404096 bytes
255 heads, 63 sectors/track, 972802 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/sdf: 32.0 GB, 32031866368 bytes
255 heads, 63 sectors/track, 3894 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x018e3066

Device Boot Start End Blocks Id System
/dev/sdf1 * 1 3895 31281088 c W95 FAT32 (LBA)
jason@server:~$

jason@server:~$ df -kf
df: invalid option -- 'f'
Try `df --help' for more information.
jason@server:~$ df -kh
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 143G 3.8G 132G 3% /
none 1.8G 728K 1.8G 1% /dev
none 1.9G 796K 1.9G 1% /dev/shm
none 1.9G 1.4M 1.9G 1% /var/run
none 1.9G 0 1.9G 0% /var/lock
/dev/mapper/server-server
5.4T 5.1T 0 100% //storage
/dev/sdf1 30G 4.7G 26G 16% //PENDRIVE
jason@server:~$

---

