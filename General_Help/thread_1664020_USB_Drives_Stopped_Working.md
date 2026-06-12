---
title: "USB Drives Stopped Working"
date: 2011-01-10
forum: General Help
---

### Post by cirelosborn on 2011-01-10
USB Drives show up in the Disk Utility, but no where else.  I cannot mount any USB drive.  They all mounted fine up till a week ago.

---

### Post by elliotbeken on 2011-01-10
Do you have another PC you can use to see if it workes on another device?

maybe the disk have become damaged or corrupt?

---

### Post by cirelosborn on 2011-10-15
Sorry to reply so late.  What happened was that I had an external backup drive that was connected through usb and when my computer started it deemed that backup drive as my sda (master) and my internal hard drive as sdb (slave).  The solution was; do not plug in the backup drive until the computer has booted into ubuntu.  After I found that out then all of my other flash drives were being mount properly as sdb2, sdb3, ect... and not as sda2, sda3, ect... which really messed things up.

---

