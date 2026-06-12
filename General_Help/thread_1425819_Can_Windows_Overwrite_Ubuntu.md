---
title: "Can Windows Overwrite Ubuntu?"
date: 2010-03-09
forum: General Help
---

### Post by DOS Boot on 2010-03-09
Hello, is it possible to use a Windows-based recovery partition on a dual-boot computer to overwrite the Ubuntu partition and remove the GRUB loader? For instance, if you booted up your computer, accessed the hidden recovery partition and used it to reset the computer to it's factory default settings, would that effectively remove the Ubuntu partition and the GRUB loader?

Would a completely new installation of Windows overwrite/uninstall Ubuntu and GRUB automatically?

---

### Post by cpressland on 2010-03-09
Depends how the OEM has things setup.

99.9% of the time, it deletes all partitions and reinstalls everything.

---

### Post by Revolutionary101 on 2010-03-09
A new installation of Windows would overwrite Ubuntu and GRUB. Ironically, you can solve your Windows problems on an Ubuntu forum.

---

### Post by doas777 on 2010-03-09
only if it replaces the mbr, which most partitioning tools do not do. perhaps this utility fully reinitalizes the disk, who knows.

---

### Post by lakersforce on 2010-03-09
Assuming Windows XP: a OEM install will overwrite everything. A install that's not OEM (i.e. normal) only overrides the MBR, and the partition you choose to use, not other partitions. But there's a bug in the windows installer partition program, that makes it impossible to make more than 3 primary partitions. Of course you can prepare your 4th primary partition from a GNU/Linux livecd.

---

