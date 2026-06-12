---
title: "Mounting RAID hard drives"
date: 2012-05-10
forum: General Help
---

### Post by The Midnighter on 2012-05-10
Hi all,

So I downloaded the Alternative installation for Ubuntu 12 and ran through the manual to setup my 2 hard drives as a RAID1 - this seems to have worked as I'm now in Ubuntu.

However, I'm not able to see my hard drive space / folders, the only folder I can access is "File system" and my "Home" directory.

/mnt is empty, /media only has cdrom.

What did I do wrong? :(

---

### Post by The Midnighter on 2012-05-10
Here's my FDISK -L output:

fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00036a28

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   960083967   480040960   fd  Linux raid autodetect
/dev/sda2       960086014   976771071     8342529    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       960086016   976771071     8342528   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0006070f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   960083967   480040960   fd  Linux raid autodetect
/dev/sdb2       960086014   976771071     8342529    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5       960086016   976771071     8342528   82  Linux swap / Solaris

Disk /dev/md0: 491.6 GB, 491560755200 bytes
2 heads, 4 sectors/track, 120009950 cylinders, total 960079600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/mapper/cryptswap1: 8542 MB, 8542748672 bytes
255 heads, 63 sectors/track, 1038 cylinders, total 16685056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc0223bc1

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

Disk /dev/mapper/cryptswap2: 8542 MB, 8542748672 bytes
255 heads, 63 sectors/track, 1038 cylinders, total 16685056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x6868bb6b

Disk /dev/mapper/cryptswap2 doesn't contain a valid partition table

---

### Post by The Midnighter on 2012-05-11
Not a single reply - clearly I've chosen the wrong distro.

---

### Post by steeldriver on 2012-05-11
I'm not sure exactly what you're expecting to see? are you using any volume management on top of RAID (lvm) or did you conventionally partition and mkfs the bare array?

I'm a RAID n00b myself, but your fdisk output looks pretty similar to what I get (running lvm2) - have you tried

```

sudo mdadm --detail /dev/md0

```

---

### Post by The Midnighter on 2012-05-11
I'm just looking to be able to see my drive(s) mounted.

---

### Post by piratebill on 2012-05-11
Have you manually tried to mount md0 (mount /dev/md0p1 /media/some_folder)?

what does your fstab look like?


Edit:
Did you create a partition on the raid? (the p1).  Fdisk says there is no partition on the raid volume.  You can't mount a device with no partition

---

