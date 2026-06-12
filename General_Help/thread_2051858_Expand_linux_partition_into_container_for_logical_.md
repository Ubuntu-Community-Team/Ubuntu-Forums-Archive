---
title: "Expand linux partition into container for logical partitions"
date: 2012-09-02
forum: General Help
---

### Post by MYz160 on 2012-09-02
For some reason, when ubuntu was installed, it created an extended partition (sda1) alongside the partition where linux is installed (sda5) and of the same size, it is also bootable.  

I was wondering if it was safe to delete the extended partition selected here, and to expand my linux partition (ext4) into it. Surely boot information should not up 200+ gigs? Why did it do this?

[IMG]http://i.imgur.com/4vo3Q.png[/IMG]

sudo fdisk -l output:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8160c50f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2046   512002047   256000001    5  Extended
/dev/sda2      1208322048  1232322559    12000256   82  Linux swap / Solaris
/dev/sda3       512002048  1208322047   348160000    7  HPFS/NTFS/exFAT
/dev/sda5            2048   512002047   256000000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8000 MB, 8000110592 bytes
255 heads, 63 sectors/track, 972 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15624191     7811072    c  W95 FAT32 (LBA)
```

---

### Post by 2F4U on 2012-09-02
You can boot from a live CD or USB into Ubuntu. Then open the application *gparted* which will already be present and resize partitions. This can however break your bootloader and might require fixing it. A better idea may be to create a new partition and move your home folder to the new partition.

---

### Post by steeldriver on 2012-09-02
I think you misunderstand how extended partitions work - your sda5 is a logical partition *inside *the extended partition - look at the start / end block, you can see they overlap

It's set up this way because of the 4 primary partition maximum

---

### Post by MYz160 on 2012-09-02
Thanks steeldriver, you prompted me to add the partitions together to reach 1 TB.  I found it misleading that both the extended and logical partition display 262 GB. Thanks again.

---

