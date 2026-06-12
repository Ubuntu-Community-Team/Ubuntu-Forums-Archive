---
title: "Vanilla Kernel 2.6.26-8 in 9.10"
date: 2009-12-22
forum: General Help
---

### Post by adamsih300u on 2009-12-22
Hello all,

I have a special need to run an older kernel than is available in the current sources due to a hardware driver having been changed around kernel version 2.6.26. I thought of installing an older copy of Ubuntu (or Debian, as I just happened to try), but while the hardware that I need a working kernel driver for is quite old, the computer itself is quite new and so I have to start with the newest install discs, and retrograde the kernel from there.

Anyways, my issue is that I have downloaded vanilla kernel, and followed the make-kpkg instructions to compile and install the resulting .deb files. The kernel compiles fine, and installs fine, but when the system boots it always hangs after "Freeing Unused Kernel Memory". I have disabled modules and initrd and basically stripped everything out of the kernel that I don't need. Anything I do need is compiled directly into the kernel.

It's difficult to provide logs of this, since the server doesn't get to a point where it can begin writing logs to disk for later analysis (I can reboot and recompile, of course, using the default 2.6.31 kernel).

The system is an AMD Athlon II with AMD/ATI chipsets. The driver that I need the older kernel for loads and processes fine, at least no errors are shown on screen, my only issue at the moment is the hanging at the point I mentioned. I have tinkered with quite a few of the config settings, including disabling ACPI and APM. I had used Gentoo a lot in the past, so I'm not afraid of messing with the kernel configs.

Any help or suggestions for an alternative are greatly appreciated. Note that I'm running 32-bit for simplicity sake.

-Adam

---

### Post by dcstar on 2009-12-22
> **adamsih300u said:**
> Hello all,

I have a special need to run an older kernel than is available in the current sources due to a hardware driver having been changed around kernel version 2.6.26. I thought of installing an older copy of Ubuntu (or Debian, as I just happened to try), but while the hardware that I need a working kernel driver for is quite old, the computer itself is quite new and so I have to start with the newest install discs, and retrograde the kernel from there.
..........
Any help or suggestions for an alternative are greatly appreciated. Note that I'm running 32-bit for simplicity sake.

-Adam

Or you could simply manually download and install an older kernel from here:

[http://packages.ubuntu.com/search?suite=jaunty&searchon=names&keywords=linux-image](http://packages.ubuntu.com/search?suite=jaunty&searchon=names&keywords=linux-image)

---

