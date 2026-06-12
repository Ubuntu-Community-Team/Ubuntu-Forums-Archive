---
title: "Did I screw up my Windows XP Installation?"
date: 2009-08-06
forum: General Help
---

### Post by sevaka on 2009-08-06
Hi,
I started Ubuntu 9.04 on my Laptop IBM-Lenovo T41 (normally running Windows XP Professional)
from the Live CD. Then I chose to install Ubuntu on a USB pendrive. That completed, but the laptop did not boot up into Ubuntu from that USB pendrive.
Now I want to boot up into Windows XP but only get a black screen with:
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 21

What went wrong? How do I get Windows back to boot up?

Any helpful advice will be highly appreciated. Thank you.

---

### Post by montini on 2009-08-06
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
repairs any problems related to booting process.

And BTW look there maybe: [http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717)

---

### Post by Mike_IronFist on 2009-08-06
> **sevaka said:**
> Hi,
I started Ubuntu 9.04 on my Laptop IBM-Lenovo T41 (normally running Windows XP Professional)
from the Live CD. Then I chose to install Ubuntu on a USB pendrive. That completed, but the laptop did not boot up into Ubuntu from that USB pendrive.
Now I want to boot up into Windows XP but only get a black screen with:
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 21

What went wrong? How do I get Windows back to boot up?

Any helpful advice will be highly appreciated. Thank you.

Well, it sounds to me like you made a very unfortunate mistake.

Ubuntu has a seperate installer for USB pendrives, you see, and it sounds to me like you installed to the Pen Drive using Ubuntu's regular installer, rather than the USB Startup Disk Creator (which is available under "System-->Administration" menu while using the Live CD).

EDIT: Just use the Super Grub disk to remove GRUB. It should be easy and painless for you.

---

### Post by konqui on 2009-08-06
No problem! Just reinstall ubuntu with normal installer.
On the last step click advanced options. Enter bootloader (hd0) means first hard disk.(hd1) second disk. 

If you have only one hard disk (hd1) will install to pendrive.
If you have two hard disks (hd2) will install to pendrive.
................................

---

### Post by sevaka on 2009-08-06
Thank you so much. The Supergrubdisk made my day. Thank you guys for such a wonderful utility.

---

