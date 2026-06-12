---
title: "Secondary hard drives &quot;auto-detect&quot;"
date: 2010-06-29
forum: General Help
---

### Post by Werm on 2010-06-29
This is probably a stupid questions but it's a pet peeve of mine. I have three hard drives you have to actually open them before they show up in other areas/on the desktop.

Is there a way that when ubuntu starts they just automatically are detected?

I hope that makes sense, thanks ):P

---

### Post by mikewhatever on 2010-06-29
You'll need to automount the drives by adding a few lines to /etc/fstab. Can you post the outputs of the following:

cat /etc/fstab

sudo fdisk -l

---

### Post by Werm on 2010-06-30
> **mikewhatever said:**
> You'll need to automount the drives by adding a few lines to /etc/fstab. Can you post the outputs of the following:

cat /etc/fstab

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8204853c-4e9d-47c0-b8ef-d127e5406a33 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0755a669-9731-407d-bc66-15fb1d7eee66 none            swap    sw     

> **mikewhatever said:**
> sudo fdisk -l

> Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000195e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17496   140530688   83  Linux
/dev/sda2           17496       18242     5990401    5  Extended
/dev/sda5           17496       18242     5990400   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046de0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf891bd55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77826   625130808+  42  SFS


.

---

### Post by dino99 on 2010-06-30
mountmanager is an easy tool to set your prefs about partitions and devices, install it with synaptic, then goto system admin mountmanager

---

