---
title: "Booting Two hard drives"
date: 2011-01-23
forum: General Help
---

### Post by Eddie Parker on 2011-01-23
I have installed two hard drives. One is a Sata drive and the other an IDE drive.They are both functional drives. On boot up only the Sata drive shows up. How do I get both drives to boot up together please.The Sata drive has Ubuntu on it and the IDE drive has Fedora on it' I would like to access all of them.

---

### Post by wilee-nilee on 2011-01-23
> **Eddie Parker said:**
> I have installed two hard drives. One is a Sata drive and the other an IDE drive.They are both functional drives. On boot up only the Sata drive shows up. How do I get both drives to boot up together please.The Sata drive has Ubuntu on it and the IDE drive has Fedora on it' I would like to access all of them.

Go into the bios at powering on and change the hd's to be read as ahci/ide what ever is indicated to read the older type drive, and see if that works.

---

### Post by Eddie Parker on 2011-01-24
Thank you. But where do I find ahc/ide in the Bios.The Ide drive is not detected.
Regards
Eddie

---

### Post by wilee-nilee on 2011-01-24
> **Eddie Parker said:**
> Thank you. But where do I find ahc/ide in the Bios.The Ide drive is not detected.
Regards
Eddie

On all my computers there is a toggle for how the drive is read that is what your looking for, may or may not be there. Your not looking for if the ide is seen yet. I think you will have to restart it to see if it is read after changing how the hd is read.

---

