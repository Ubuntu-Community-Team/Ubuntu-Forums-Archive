---
title: "Grub Error 2, No boot folder in root"
date: 2009-10-22
forum: General Help
---

### Post by levif on 2009-10-22
So I've encountered an interesting problem.  Ubuntu has been running on my computer for some time.  Recently, upon boot, I received Error 2 in grub.  No big deal, just fix the stage1 file and move on, right?  Well, the "boot" directory is no longer a directory in my root directory.  It is a single, uneditable, unopenable file.  I am using ubuntu 8.04. Any ideas? I really don't want to perform a fresh install.

---

### Post by dcstar on 2009-10-23
> **levif said:**
> So I've encountered an interesting problem.  Ubuntu has been running on my computer for some time.  Recently, upon boot, I received Error 2 in grub.  No big deal, just fix the stage1 file and move on, right?  Well, the "boot" directory is no longer a directory in my root directory.  It is a single, uneditable, unopenable file.  I am using ubuntu 8.04. Any ideas? I really don't want to perform a fresh install.

Do a fsck on the partition (use a Live CD).

---

### Post by levif on 2009-10-23
I've already run two.  Upon further review, it appears that I'm missing far more than just the boot directory.  "bin" and "etc" are missing, notably.  At this point, I'm just planning to reinstall.

---

