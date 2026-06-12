---
title: "crc error after deleting kernel"
date: 2009-08-15
forum: General Help
---

### Post by ziofil on 2009-08-15
Hi all!
I kind of made a disaster..
I wanted to free some space in / and I deleted some old kernels, not realizing that i was deleting also the actual one that i needed to boot...
As a result every time that I boot i immediately end up in the grub shell. Even if i tell grub that root is in (hd0,0) and then to setup in (hd0), the system doesn't boot.
Now the weird thing: if I try to boot from liveCD i get to the first ubuntu screen, I choose to start ubuntu in live mode and then i get the lines: crc error -- system halted.
(i even tried different live CDs, same thing, even the usb boot...)

I googled crc error and it seems a hardware error (cyclic redundancy check), right now i'm running a memtest to see if it's the ram, but i hardly think it's hardware, as the problem started exactly when I deleted the kernel.
Any ideas? (I'm running Jaunty 64 bit on a desktop with AMD athlon 64X2 5600+, 2Gb ram, NVIDIA 8800GT 512Mb)

---

### Post by SoftwareExplorer on 2009-08-16
Does the liveCD bootup properly if you unplug your hard drive? Just an idea to figure out if it is something on the hard drive.

---

