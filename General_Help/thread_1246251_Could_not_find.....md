---
title: "Could not find...."
date: 2009-08-21
forum: General Help
---

### Post by Mutil8r on 2009-08-21
Hi, im trying to edit my menu.lst of grub so that I can dual boot Ubuntu and Windows 7.

im booting at my disk now and when I opened my menu.lst its a blank FILE! and when I save this pops up.

Could not find the file /boot/grub/menu.lst.

Help pls. I have to know fast so I can finish this.

---

### Post by lisati on 2009-08-22
Did you install Ubuntu using Wubi or into its own partition?
Does anything show when you type in the follwoing? ```
locate menu.lst
```

---

### Post by michy99 on 2009-08-22
When you boot from a Live CD, the ubuntu partition does not get mounted unless you mount it. If you mount it at /mnt/disk for example, your menu.lst file will be at /mnt/disk/boot/grub/menu.lst.

---

