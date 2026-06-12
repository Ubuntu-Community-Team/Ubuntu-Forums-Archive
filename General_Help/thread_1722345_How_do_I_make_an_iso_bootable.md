---
title: "How do I make an iso bootable?"
date: 2011-04-05
forum: General Help
---

### Post by searayman on 2011-04-05
I am trying to boot from an external hard drive, and have tried to use unetbootin like I used when crating a bootable usb drive but it does not see my external and will not create  bootbale iso for me to run from my external hard drive.


Any ideas?

---

### Post by dabl on 2011-04-05
You don't "make" an ISO image file bootable -- it either is, or it isn't, based on the design of it.

Your PC has a BIOS.  In that BIOS, you may or may not have options to set it to boot from a "removable device" or "USB".  Moreover, you have a "boot priority" BIOS setting.  So, to boot from a USB-connected device like a USB memory stick or an USB-connected external hard disk drive, you must go into BIOS and set it to see the removable device as the first boot priority device.

If your computer is an older model that does not support booting from USB, then it's not gonna work.

Hope this helps.

---

### Post by pqwoerituytrueiwoq on 2011-04-05
grub 2 has a feature to boot iso field off a hard disk
unetbooting can use the internal hdd

---

