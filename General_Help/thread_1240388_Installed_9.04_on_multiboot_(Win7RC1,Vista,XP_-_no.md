---
title: "Installed 9.04 on multiboot (Win7RC1,Vista,XP - no Ubuntu choice"
date: 2009-08-14
forum: General Help
---

### Post by errolgreer on 2009-08-14
Hi

I have a multiboot system with Win7-RC1 on the first HD, and XP and Vista on the second HD. I installed 9.04 in free space on the second HD. After the install was done, it asked to click on reboot, which I did. However, only the boot choices I had before - 1 Win7, 2 Vista, 3 XP appeared, with no sign of Ubuntu ! GRUB did not appear at all. It's just as if I never installed Ubuntu. What do I do to get an Ubuntu boot prompt ?:(

---

### Post by aethex on 2009-08-14
Not sure, but I read somewhere that GRUB doesn't work on a second physical HDD. It apparently has to be on the first.

Or somehow set the second HDD as the primary, and boot from the partition that has GRUB (the Ubuntu one). I have no clue how to do this, though.

---

