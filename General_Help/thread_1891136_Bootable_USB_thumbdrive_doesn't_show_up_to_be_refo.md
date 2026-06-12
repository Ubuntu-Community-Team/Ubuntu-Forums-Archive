---
title: "Bootable USB thumbdrive doesn't show up to be reformatted"
date: 2011-12-05
forum: General Help
---

### Post by erinod on 2011-12-05
Hi all,

I have a usb thumbdrive that is formatted as a bootable start up disk for ubuntu. Now that my ubuntu os is installed, I want to take back my thumb drive for other uses, but it doesnt show up in my disk utility so that I can reformat it. Any help would be appreciated.

Thanks!

---

### Post by C.S.Cameron on 2011-12-05
Have you tries gparted?

---

### Post by max2009ro on 2011-12-05
Try ```
sudo modprobe usb-storage
``` if module usb-storage is not loaded at startup.

---

