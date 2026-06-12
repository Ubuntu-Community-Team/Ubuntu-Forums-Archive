---
title: "Can Ubuntu be installed on a slave drive?"
date: 2010-01-26
forum: General Help
---

### Post by Cityscape on 2010-01-26
I have a computer with 2 hard disks. I want to dual-boot Ubuntu with Windows 98. I want to install 98 on the Primary Master. Will Ubuntu work being installed on the Primary Slave?

---

### Post by mechro on 2010-01-26
Don't know what you mean by "Primary" but you can install Ubuntu on a slave drive.

Whether it will boot easily depends on your BIOS.

You have a choice of installing the bootloader on the master and booting everything from there or you could have Windows bootloader on the master and Ubuntu bootloader(Grub) on the slave. Again, depends on BIOS.

---

### Post by lindsay7 on 2010-01-26
Yes you can install it wherever you want it.  Use the manual method during the install and tell the install program where you want to put ubuntu.

---

### Post by cascade9 on 2010-01-26
> **Cityscape said:**
> I have a computer with 2 hard disks. I want to dual-boot Ubuntu with Windows 98. I want to install 98 on the Primary Master. Will Ubuntu work being installed on the Primary Slave?

No problem. But for myself, I always run PATA HDDs as master, not slave (at least until I run out of channels)

---

