---
title: "Non-standard mount points"
date: 2009-12-29
forum: General Help
---

### Post by cwarner7_11 on 2009-12-29
Working with both 9.04 and 9.10, I have encountered a couple of instances where it appears Ubuntu is using non-standard mount points for various parts of the file system.  Specifically, Ubuntu seems to prefer mounting the usb file system under /dev/bus/usb, which seems like a logical place to put it, until one tries to use other, non-Canonical packages with usb support (i.e., non-free VirtualBox, and USBView, a sort of GUI for lsusb), it seems others are looking for the usb file system under /proc/bus/usb.  Once one figures out what is going on, this is easy enough to fix, but it creates a negative image of Ubuntu among the general users.  Antoher instance that may or may not be the same is that QEMU is looking for /dev/kqemu, which apparently is not created during the normal *.deb build.  Thus, QEMU does not have access to the accelerator level, and this apparently causes it to freeze up (there may be other problems unrelated to this with QEMU- we are still trying to get it to work).
I tried to report this as a bug in launchpad, but launchpad told me they were having technical difficulties...

---

### Post by dcstar on 2009-12-29
> **cwarner7_11 said:**
> Working with both 9.04 and 9.10, I have encountered a couple of instances where it appears Ubuntu is using non-standard mount points for various parts of the file system.  Specifically, Ubuntu seems to prefer mounting the usb file system under /dev/bus/usb, which seems like a logical place to put it, until one tries to use other, non-Canonical packages with usb support (i.e., non-free VirtualBox, and USBView, a sort of GUI for lsusb), it seems others are looking for the usb file system under /proc/bus/usb.  Once one figures out what is going on, this is easy enough to fix, but it creates a negative image of Ubuntu among the general users.
..........

The good thing about "standards" is that there are so many to choose from.

What is/was "standard" can be deprecated and different distros can still adopt different ways of doing things - choosing one "standard" over another.

---

