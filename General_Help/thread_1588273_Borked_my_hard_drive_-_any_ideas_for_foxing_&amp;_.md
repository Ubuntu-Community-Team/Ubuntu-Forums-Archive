---
title: "Borked my hard drive - any ideas for foxing &amp; recovering data? Please help!"
date: 2010-10-04
forum: General Help
---

### Post by anandamide on 2010-10-04
OK, was trying to make a live-usb boot partition on my 1.5TB HD; in doing so clicked a 'wipe disk' button.

A second later I realised what I'd done, clicked cancel (frantically), tried to unmount the drive but was told 'volume busy'. In a panic, unplugged the drive.

Unsurprisingly, the drive is now a mess. 

I'd had 1 30G FAT32 partition (empty) at sdd1, 1 1.5TB ext4 partition with about 500G of data at sdd2. Now according to gparted I have an unrecognised filesystem type; according to the 'Disk Utility' I have an unmountable 1.5TB FAT32 drive.

I know NOTHING about data recovery. If it's just a case of running a couple of magic 'check & fix' programs then I should be OK, but anything else and I'll have to take it to more skilled friends.

Do I have any hope?

---

### Post by yetiman64 on 2010-10-04
> **anandamide said:**
> OK, was trying to make a live-usb boot partition on my 1.5TB HD; in doing so clicked a 'wipe disk' button.

A second later I realised what I'd done, clicked cancel (frantically), tried to unmount the drive but was told 'volume busy'. In a panic, unplugged the drive.

Unsurprisingly, the drive is now a mess. 

I'd had 1 30G FAT32 partition (empty) at sdd1, 1 1.5TB ext4 partition with about 500G of data at sdd2. Now according to gparted I have an unrecognised filesystem type; according to the 'Disk Utility' I have an unmountable 1.5TB FAT32 drive.

I know NOTHING about data recovery. If it's just a case of running a couple of magic 'check & fix' programs then I should be OK, but anything else and I'll have to take it to more skilled friends.

Do I have any hope?Sounds like you may need to use something like testdisk (available in the repositories).

It is not a simple program to use as such, but can be very effective at finding and repairing damaged partition tables if used correctly. Check [[s] THIS LINK [/s] ]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")for its usage guide (step by step instructions).

---

### Post by anandamide on 2010-10-04
Thanks - that should get me started if nothing else. Doesn't seem too tricky. Hoping it's a fairly straightforward problem.

---

