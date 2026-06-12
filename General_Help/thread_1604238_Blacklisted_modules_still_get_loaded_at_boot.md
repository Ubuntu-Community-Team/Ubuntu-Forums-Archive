---
title: "Blacklisted modules still get loaded at boot"
date: 2010-10-23
forum: General Help
---

### Post by scarleo on 2010-10-23
I'm trying to prevent a few modules from loading at boot, like i.e. bluetooth, sco, bnep, btusb, usb_storage and uvcvideo, so I blacklisted them in /etc/modprobe.d/blacklist.conf but they still get loaded. I've checked that I unload all of the ones depending on eachother so that shouldn't be the problem, I think. Does anyone know what I'm supposed to do to really prevent them from loading?

I'm running Lucid.

---

### Post by efflandt on 2010-10-23
They are already in the kernel when it boots.  See **man update-initramfs**.

**sudo update-initramfs -c** (defaults to most recent kernel only)

**sudo update-initramfs -c -k all** (all kernels)

I discovered that when trying to disable floppy module when errors from Linux trying to check for non-existing floppy in hot swap drive bay prevented suspend/hibernate.  Since it was preloaded, blacklisting did no good until I did the update-initramfs.

---

### Post by scarleo on 2010-10-23
Ah, ok. Thanks a lot, I'll look into that.

---

