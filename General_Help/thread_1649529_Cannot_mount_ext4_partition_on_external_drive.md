---
title: "Cannot mount ext4 partition on external drive"
date: 2010-12-20
forum: General Help
---

### Post by jan2jen on 2010-12-20
Hi, I have created 2 partitions on my external usb HDD. The first one is NTFS and the second one is EXT4. Ubuntu mounted automaticaly both partitions properly about 20 times. Suddenly Ubuntu mounts only the NTFS partition.

Below is what I've tried. I have also tried "system->administration->disk utility" and there was written:
Usage: -
Partition Type: Linux (0x83)
Partition Flags: -
Device: /dev/sdb2
-- and no avalability to mount the partition --

```
$ sudo fdisk -l

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1a591467

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          12       96358+   7  HPFS/NTFS
/dev/sdb2              13       60801   488287642+  83  Linux
```


```

$ sudo mount -t ext4 /dev/sdb2 /media/adata/
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```


dmesg | tail
[   37.545152] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   37.545749] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   37.545752] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   37.545754] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   46.686289] lo: Disabled Privacy Extensions
[   47.220043] wlan0: no IPv6 routers present
[   80.589050] ACPI: EC: GPE storm detected, transactions will use polling mode
[  297.802590] CE: hpet increased min_delta_ns to 7500 nsec
[  878.862589] CE: hpet increased min_delta_ns to 11250 nsec
[  945.996785] EXT4-fs (sdb2): VFS: Can't find ext4 filesystem


```

---

### Post by oldfred on 2010-12-20
I would try this first. Since it is not mounted, you probably can just run from your install.

From liveCD so everything is unmounted, change sdb2 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sdb2
if errors:
sudo e2fsck -f -y -v /dev/sdb2

---

### Post by jan2jen on 2010-12-21
Thanks for reply. However, this does not work. "Can't find ext4 filesystem" it seems that the partition was somehow damaged. I will format the whole disk.

---

