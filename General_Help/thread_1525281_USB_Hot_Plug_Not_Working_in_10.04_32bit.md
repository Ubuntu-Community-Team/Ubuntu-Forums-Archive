---
title: "USB Hot Plug Not Working in 10.04 32bit"
date: 2010-07-06
forum: General Help
---

### Post by bdprem on 2010-07-06
I am running the 32 bit version of Ubuntu 10.04 on an old Acer Aspire 1522LMi.

If I boot up in the 2.6.32-21 kernel, I can plug in usb devices such as a flash drive and it is recognized just fine.

If I use either the 2.6.32-22 or -23 kernels, and plug in my flash drive, mouse or card reader they are not recognized.  They show up in lsusb.  Dmesg shows a device was plugged in, but doesn't recognize it or try to load a driver for it.  In -21, the correct messages appear in both lsusb and dmesg.

If I plug in the devices first and then boot up in -22 or -23, the devices are loaded just fine.

Does anyone know how to turn the usb hotplug back on or if their is a patch coming to fix this?

---

### Post by bdprem on 2010-07-06
Further reading says that HAL is no longer used.  Now udev is the only device manager in use.  It requires rules written for attaching and removing devices.  Is anyone tackling this?

---

### Post by bdprem on 2010-07-06
I was redirected to a bug report on this issue.  One of the fixes was to add usb-storage and usbhid to the /etc/modules file.  The original modules file only had the lp module listed.  Now it is working as it should.

---

