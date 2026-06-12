---
title: "Delete GPT Partition"
date: 2010-02-15
forum: General Help
---

### Post by sreilly on 2010-02-15
Hi,

I have a new WD 1TB drive on a remote machine running Ubuntu 8.10 that steadfastly refuses to remove its GPT partition.

It is a WD10EADS-65M and when I run fdisk it complains about "WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table"

How do I remove the GPT partition?

I have tried dd'ing the entire drive with

dd if=/dev/zero of=/dev/sdc bs=512 count=2
dd if=/dev/zero of=/dev/sdc bs=512 seek=1000204886016

But the GPT still persists.

TIA,

Steve

---

### Post by bluefrog on 2010-02-15
it is telling you to use parted.

I guess following the advice could be a good start...

if you really want to get rid of the GPT then use mklabel within parted. All data will be lost.

Or just use parted instead of fdisk.

---

### Post by sreilly on 2010-02-15
Yep, I spotted that it suggested using parted but I didn't want to start learning another partitioning tool if I could get rid of the GPT and configure it using fdisk (like I do with the other three disks on the same machine).

I just tried mklabel msdos, and mktable msdos, but the GPT is reported in fdisk.

Steve

---

### Post by bluefrog on 2010-02-15
basically fdisk sucks (personal opinion, I will not carry on a troll...).

Most things you do with fdisk need a reboot to be taken in account. Most things you do with another tool need a reboot for fdisk to take it in account.

if you change your disk label from GPT to msdos with parted it is ok for parted, you can do whatever you want. For fdisk you will need to reboot

UPDATE: fdisk in 9.10 behaves much better than before...

---

### Post by sreilly on 2010-02-15
After a reboot fdisk still Warns about the disk. However, gparted doesn't complain and allows me to partition the drive.

I guess I will have to read up on parted.

Many thanks.

Steve

---

