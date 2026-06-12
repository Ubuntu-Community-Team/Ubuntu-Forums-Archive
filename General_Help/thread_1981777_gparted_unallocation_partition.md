---
title: "gparted unallocation partition"
date: 2012-05-17
forum: General Help
---

### Post by soniappr on 2012-05-17
Hi,

I have a laptop with one hard drive and several partitions and windows vista and linux installed. I was going to upgrade linux but errors made it impossible so I was about to reinstall it. But the live CD does not detect my partitions and gparted sees only one big unallocated space, and prints the message
```
Can't have overlapping partitions.
```

Here is the result of sudo fdisk -lu, I don't really know how to read it...

```
kubuntu@kubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x68000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   483153920   488394751     2620416    c  W95 FAT32 (LBA)
/dev/sda2          258048    21229567    10485760    7  HPFS/NTFS/exFAT
/dev/sda3   *    21229568   138417067    58593750    7  HPFS/NTFS/exFAT
/dev/sda4       138432166   488394751   174981293    f  W95 Ext'd (LBA)
/dev/sda5       483153920   488394751     2620416   dd  Unknown
/dev/sda6       138432168   154047284     7807558+  82  Linux swap / Solaris
/dev/sda7       154047348   349365554    97659103+   b  W95 FAT32
/dev/sda8       349365618   427489649    39062016   83  Linux
/dev/sda9       427489713   483138809    27824548+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcfff9bdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS/exFAT
```

Can someone help me ? I don't know what to do, I don't have external disk space to save all data, I just saved my /home. I'd like to overwrite or format sda8 which was / and maybe sda9 (/home) but I don't want to touch sda3 (windows) or sda7 (my data).

Any suggestions will be very helpful, thanks in advance,
cheers,
Sonia

---

