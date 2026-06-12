---
title: "Some partition issues, a little frustrated!"
date: 2009-11-12
forum: General Help
---

### Post by djbon2112 on 2009-11-12
Here's my current disk setup:

320 GB disk (/dev/sda), GPT partition table, all primary partitions (since GPT can't created extended partitions)
/dev/sda1: 100MB, /boot
/dev/sda2: 2GB, swap
/dev/sda3: 30GB, /
/dev/sda4: 60GB, /home

The remaining space is free, which is where my problem comes in. I'm trying to create another partition (/dev/sda5) with the remaining space (about 180GB). The only way I can create it is as primary (since GPT can't create extended partitions). The problem is, as soon as I create this 5th partition, my system will not boot. It's as if /dev/sda1 no longer exists. In fact, GRUB won't even load from the MBR of the disk (so whatever is happening is also corrupting the MBR). This makes sense from a theoretical perspective (i.e. the 4-primary-partition limit), BUT, I thought the point of GPT was to eliminate that! Are there any workarounds here that don't involve me wiping the whole disk and putting an msdos table on it?

---

