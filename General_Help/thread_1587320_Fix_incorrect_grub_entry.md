---
title: "Fix incorrect grub entry"
date: 2010-10-03
forum: General Help
---

### Post by Warthaug on 2010-10-03
I am setting up a dual-boot win7/ubuntu system.  However, upon installing ubuntu, grub has picked the wrong partition as the windows partition.   Instead of booting the windows partition (sda3) it is loading the recovery partition (sda2).

I tried manually editing the entry at boot to read sda3, but when I booted from that entry it still booted the recovery drive.

How do I fix this?  I read the guide on grub2, but I couldn't figure out how fix it from there.

Bryan

---

### Post by Warthaug on 2010-10-03
Never mind, somewhere along the line ubuntu fixed things automatically.

B

---

