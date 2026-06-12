---
title: "Grub does not start during boot"
date: 2011-01-24
forum: General Help
---

### Post by olegio on 2011-01-24
A friend of mine installed ubuntu 10.10 alongside with Windows XP.
During the installation he manually edited partitions.

Now, the grub loader does not start, and in order to start ubuntu he has to use live cd to choose "boot from first hard drive" in the menu. Windows XP is missing from the boot options. 

See the output of "fdisk -l" below (he has two identical hard drives). It looks like a big mess. Any idea where to start fixing this?

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05c605c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25296   203187201    f  W95 Ext'd (LBA)
/dev/sda2           25297       30400    40997880    7  HPFS/NTFS
/dev/sda5   *           1       21249   170676224    7  HPFS/NTFS
/dev/sda6           21249       25296    32509952   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd5281488

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       25296   203187201    f  W95 Ext'd (LBA)
/dev/sdb2           25297       30400    40997880    7  HPFS/NTFS
/dev/sdb5               1       21249   170676224    7  HPFS/NTFS
/dev/sdb6           21249       25296    32509952   83  Linux

Disk /dev/dm-0: 250.1 GB, 250056015872 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05c605c5

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1       25296   203187201    f  W95 Ext'd (LBA)
/dev/dm-0p2           25297       30400    40997880    7  HPFS/NTFS
/dev/dm-0p5   *           1       21249   170676224    7  HPFS/NTFS
/dev/dm-0p6           21249       25296    32509952   83  Linux

Disk /dev/dm-1: 42.0 GB, 41981829120 bytes
255 heads, 63 sectors/track, 5104 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 174.8 GB, 174772453376 bytes
255 heads, 63 sectors/track, 21248 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 33.3 GB, 33290190848 bytes
255 heads, 63 sectors/track, 4047 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

---

### Post by Rubi1200 on 2011-01-24
Hi,
considering the situation, this is what I suggest:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Do not attempt to make any changes and, if you can, start making backups of important data using the LiveCD to boot and save to an external medium that will not be affected by all of this.

---

### Post by olegio on 2011-01-25
Thanks for prompt answer. Unfortunately, he took an easy way and restored Windows using some Windows recovery tool. Ubuntu is gone at this point.

---

### Post by Rubi1200 on 2011-01-25
Oh, well I suppose that is one way to deal with it!

If your friend would like to try Ubuntu, point him/her in the direction of [Wubi]("https://wiki.ubuntu.com/WubiGuide").

For a real install, there are plenty of guides on how to dual-boot.

Here is one:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

---

### Post by olegio on 2011-01-26
Thanks for the links!

---

### Post by Rubi1200 on 2011-01-26
No problem, you are more than welcome :-)

---

### Post by vandamme on 2011-01-26
Download SuperGrub and put that on a CD. Works for me.

---

