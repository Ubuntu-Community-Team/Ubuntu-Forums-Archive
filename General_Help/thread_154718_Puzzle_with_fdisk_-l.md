---
title: "Puzzle with fdisk -l"
date: 2006-04-03
forum: General Help
---

### Post by jamesr on 2006-04-03
I have a puzzle with a breezy server system.

sudo fdisk -l shows hdc1 as W95 (FAT32) which was the original config of this drive
whereas fstab is setup as
/dev/hdc1 /samfiles ext3 rw,user,auto 0 0
and mount shows
/dev/hdc1 on /samfiles type ext3 (rw,noexec,nosuid,nodev)

This partition started life as w95 partition and as converted with gparted to ext3.

---

