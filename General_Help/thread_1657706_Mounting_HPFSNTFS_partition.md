---
title: "Mounting HPFS/NTFS partition"
date: 2011-01-01
forum: General Help
---

### Post by MacUsers on 2011-01-01
Dear all,

My Windows (laptop) suddenly refused to boot, so I thought I'll mount the drive as second disk and extract some of the data off the disk. But Ubuntu refused to mount the NTFS partition as well. The disk itself appears to be fine; fdisk lists the drive correctly:

```
root@htpc:/mnt# fdisk -l /dev/sdb

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x508c2fc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9139    73400320    7  HPFS/NTFS
/dev/sdb2            9139       30402   170795008    7  HPFS/NTFS

root@htpc:/mnt# fdisk -s /dev/sdb
244198584
```lshw shows the drive correctly as well:

```
root@htpc:~# lshw -c disk
[ ..... ]
  *-disk:1
       description: ATA Disk
       product: TOSHIBA MK2555GS
       vendor: Toshiba
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: FG00
       serial: 894GF8B4S
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=508c2fc4
[.....]
```But when I try to mount one of those drives, I get this error:

```
root@htpc:/mnt# ntfs-3g /dev/sdb2 /mnt/tmp_mnt -o force
Unexpected sectors per cluster value (127).
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```Tried to fix the partition using ***ntfsfix*** but that doesn't work at all:

```
root@htpc:/mnt# ntfsfix /dev/sdb2
Mounting volume... Error opening partition device: Device or resource busy.
Failed to startup volume: Device or resource busy.
FAILED
Attempting to correct errors... Error opening partition device: Device or resource busy.
FAILED
Failed to startup volume: Device or resource busy.
Volume is corrupt. You should run chkdsk.
```Does anyone know what I'm doing wrong? Is it possible at all what I'm trying to do? Can anyone please help? Thanks in advance. Cheers!!

---

