---
title: "No valid NTFS signature"
date: 2011-07-30
forum: General Help
---

### Post by WestCoastSunset on 2011-07-30
Here is my setup

XP service pack 3 is on the c drive along with ubuntu linux 11.04.  Here is the output of fdisk -l:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8e410666

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7157    57488571    7  HPFS/NTFS
/dev/sda2            7158        9726    20634625    5  Extended
/dev/sda5            7158        9467    18547712   83  Linux
/dev/sda6            9467        9726     2085888   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70cf3d57

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?           1        4866    39086113+   7  HPFS/NTFS
steve@steveb9:~$ 


I can no longer mount the secondary drive(/dev/sdb).  It used to be automounted and everything was fine.  I did screw around with trying to make the windows bootloader the default bootloader but that did not work So I restored the grub bootloader.

The secondary drive has just an xp primary partition and this has not changed for quite some time, long before linux was on the machine.  I ran a chkdsk in windows for the secondary drive and it came back with some minor file allocation table errors which it fixed but other then that the drive was always accessible in XP with no reported problems of any kind.  For some reason I can not mount it any more, even though it used to be automounted when ubuntu was first installed.  This is the output of the mount command:

sudo mount -t ntfs /dev/sdb /mnt/edrv
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


Any ideas?

---

### Post by Mark Phelps on 2011-07-30
Try running CHKDSK on it NOW.  

If you're lucky, it will fix the filesystem problem; otherwise, it looks like your NTFS partition table is GONE.

---

### Post by WestCoastSunset on 2011-08-02
I had to download testdisk and have it write a new partition table.  I have a feeling that in XP, a partition table is not strictly needed since the drive was always accessible in windows.

---

