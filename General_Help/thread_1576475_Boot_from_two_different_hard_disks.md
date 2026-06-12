---
title: "Boot from two different hard disks"
date: 2010-09-17
forum: General Help
---

### Post by dnguyen1963 on 2010-09-17
Hi,

I have two hard disks on my computer.  Only one is physically connected to the computer at one time via the IDE cable.  The main HD is dual boot of Ubuntu and XP.  The other HD is my distro testing disk.  I plug this one in whenever there is an new and interesting distro out.

Can I hook up both HDs to the computer (either CS or master/slave) and boot each HD independently through the Bios setting?  Each HD was independently installed with diff OS.

Thanks.

---

### Post by endotherm on 2010-09-17
yes, if you bios supports, you should be able to specify the boot drive. otherwise if unspecified it should try to load the mbr from the first disk on the first chain on the first bus.
both drives partitions will need to be marked active in fdisk, and both must have an mbr and a bootloader of some kind installed.

---

### Post by dnguyen1963 on 2010-09-17
> **endotherm said:**
> yes, if you bios supports, you should be able to specify the boot drive. otherwise if unspecified it should try to load the mbr from the first disk on the first chain on the first bus.
both drives partitions will need to be marked active in fdisk, and both must have an mbr and a bootloader of some kind installed.

Thank you.

---

