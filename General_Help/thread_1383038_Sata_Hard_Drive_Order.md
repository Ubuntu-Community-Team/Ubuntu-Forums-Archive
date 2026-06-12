---
title: "Sata Hard Drive Order"
date: 2010-01-16
forum: General Help
---

### Post by lakerssuperman on 2010-01-16
I have 4 hard drives in my computer.  1 for may root and home partitions.  2 extras for storage and 1 for Windows.  I have the hard drive with my root and home partitions set as the first hard drive in the bios.  However, in the Ubuntu setup it isn't the first one in the list.  I would have thought that the first drive would be get set to sda.  That is not the case.  Does anyone know why this is?  I feel like there is an easy answer that I am missing.  Thanks.

---

### Post by dcstar on 2010-01-16
> **lakerssuperman said:**
> I have 4 hard drives in my computer.  1 for may root and home partitions.  2 extras for storage and 1 for Windows.  I have the hard drive with my root and home partitions set as the first hard drive in the bios.  However, in the Ubuntu setup it isn't the first one in the list.  I would have thought that the first drive would be get set to sda.  That is not the case.  Does anyone know why this is?  I feel like there is an easy answer that I am missing.  Thanks.

SATA drives plug into individual SATA ports on your motherboard, setting the boot order in the BIOS does not change what is plugged into the first port.

---

