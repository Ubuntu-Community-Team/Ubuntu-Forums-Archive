---
title: "GPart Shows Partition table as unallocated"
date: 2009-12-08
forum: General Help
---

### Post by arvindsa on 2009-12-08
GPart Shows Partition table as unallocated. I've read similar topics and i'm posting my fdisk stats.

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2d0b757

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275        7803    52436569+   7  HPFS/NTFS
/dev/sda3            7804       38913   249891075    5  Extended
/dev/sda4           20882       29898    72417280    7  HPFS/NTFS
/dev/sda5            7804       14357    52644973+   7  HPFS/NTFS
/dev/sda6           14358       20881    52403998+   7  HPFS/NTFS

```

I have Vista HP,

---

### Post by arvindsa on 2009-12-08
kindly help

---

### Post by Sam on 2009-12-08
Is it a laptop ? It's maybe some kind of data for a recovery process.

---

### Post by arvindsa on 2009-12-08
its a laptop

---

### Post by sgosnell on 2009-12-08
A 30-second Google search for "partition ID 27" turned up this:
```
27 PQservice

    Acer laptop hidden rescue partition. Must be FAT32. Press Alt-F10 during boot to start this. Also other manufacturers use this type for their rescue partition.
27 Windows RE hidden partition

    On MBR disks, type 0x27. On GPT disks, GUID: DE94BBA4-06D1-4D40-A16A-BFD50179D6AC. A hidden version of a Windows RE type 0x7 partition with NTFS. When this is installed, reboot and press F8 in order to boot into this Recovery Environment.

```

---

### Post by arvindsa on 2009-12-09
the question is how to install ubuntu in harddisk with vista dualboot. when trying to install it does not show existing partions. it shows entire hdd as unallocated

---

