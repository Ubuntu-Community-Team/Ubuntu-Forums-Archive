---
title: "Flash Card"
date: 2006-06-02
forum: General Help
---

### Post by Frihet on 2006-06-02
If I mount the flash card when I first start the machine (HP L2000 Laptop, 32 bit Dapper), all is well. If I try to mount after a suspend cycle, I get this:

Could not mount device.
The reported error was:
mount: can't find /dev/mmcblk0p1 in /etc/fstab or /etc/mtab

Any thoughts on this?

---

### Post by joshrobinson on 2006-06-02
[QUOTE=Frihet]If I mount the flash card when I first start the machine (HP L2000 Laptop, 32 bit Dapper), all is well. If I try to mount after a suspend cycle, I get this:

Could not mount device.
The reported error was:
mount: can't find /dev/mmcblk0p1 in /etc/fstab or /etc/mtab

Any thoughts on this?[/QUOTE]

how are you mounting it the first time? just poping it in? are you taking it out before you suspend?


have you tried adding a line for it in your fstab?

---

### Post by Frihet on 2006-06-03
I leave the card in all the time. I installed it to serve as a read/write bridge between Windows and Linux (like a FAT partition).

The first time I mount it I select "Mount" from the popup when I right-click the flash media icon on the KDE desktop. That works fine if I catch it right after booting. If I forget and let the laptop go to sleep, this will not work.

---

