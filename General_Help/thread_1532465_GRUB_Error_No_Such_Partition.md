---
title: "GRUB Error: No Such Partition"
date: 2010-07-16
forum: General Help
---

### Post by iEthan on 2010-07-16
I resize my Ubuntu extended partition in Windows and now when I boot, I'm getting a GRUB rescue and the error "no such partition". I'm on a LiveUSB. Here's the results of my fdisk -l:

```

omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6393    51351741    7  HPFS/NTFS
/dev/sda2            6394       19457   104936580    5  Extended
/dev/sda5            6394       19131   102317953+  83  Linux
/dev/sda6           19132       19457     2618563+  82  Linux swap / Solaris

Disk /dev/sdb: 2002 MB, 2002747392 bytes
32 heads, 63 sectors/track, 1940 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x7b8f2aea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1940     1955488+   b  W95 FAT32

Disk /dev/mmcblk0: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders
Units = cylinders of 810 * 512 = 414720 bytes
Disk identifier: 0x00037140

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              11       19166     7757824    b  W95 FAT32

```

The first device is my hard drive: the second is the LiveUSB and the third is an SD card I have to move files to.

I ran a fsck on my Ubuntu partition, and I can't seem to mount it (or the Windows one): it gives me the error: "Message did not receive a reply (timeout by message bus)".

How could I recover my data on both the Windows partition and the Ubuntu one?

---

### Post by oldfred on 2010-07-16
Did the UUIDs get changed.

Compare to grub and fstab:

sudo blkid

---

### Post by iEthan on 2010-07-16
I was actually able to mount both partitions in order to recover data:

```

sudo mount /dev/sda5 /mount/ubuntu

```

Now I can recover data. Thanks anyways.

---

### Post by ajgreeny on 2010-07-16
If it's just a UUID discrepancy, you could possibly save a lot of palaver or reinstalling, if that is your next move, by a simple edit of fstab.

---

