---
title: "Enable keycodes greater than 255?"
date: 2012-03-27
forum: General Help
---

### Post by agc93 on 2012-03-27
Hi all,

I'm just configuring an input panel, which is passing events to my Ubuntu 11.10 machine through /dev/input/eventX subsystem.

I've had to compile a kernel module for this panel, and many of the hardware codes are set to return standard keynames, such as:

KEY_EDITOR
KEY_VIDEO
KEY_AUDIO
KEY_TV
KEY_NEXT

Some keys, such as KEY_FINANCE and KEY_CAMERA work as a valid Accelerator in the standard System Settings/Keyboard Shortcuts dialog. From what I can tell, this is caused by their keycodes being above 255. Is there any way to patch the kernel (or similar) to allow these greater-than-255 keycodes to work in the system?

Thanks,
--Alistair

Ubuntu 11.10 (Unity)
x86 - Core 2 Quad Q6600
kernel 3.0.0-16-generic

PS: Sorry if posted before, but only similar entry I could find was for Hardy, so figured it might've changed.

---

### Post by con-f-use on 2013-04-16
Sorry for reviving an old thread, but mapping keycodes greater than 255 is generically not possible (and will not be for the forseeable future). Limited workarounds do exist. See [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/313514](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/313514)

---

