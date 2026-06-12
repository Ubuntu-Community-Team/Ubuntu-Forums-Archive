---
title: "Move grub to another drive?"
date: 2006-02-02
forum: General Help
---

### Post by Denta on 2006-02-02
When I installed Ubuntu I had two harddrives, Grub was appereantly installed to #1 and Ubuntu itself on disk #2. Now I need disk #1 in another computer so grub (MBR?) must be moved to disk #2... Howto?

---

### Post by cotcot on 2006-02-02
I guess you have the menu.lst, stage 1, 1.5 and 2 in your ubuntu /boot/grub. grub-install /dev/hdb   (supposing hdb is your disk #2) will install the bootloader in the MBR of disk #2. You have to disable your disk #1 in the bios and then reboot.
Please read the grub manual.

---

