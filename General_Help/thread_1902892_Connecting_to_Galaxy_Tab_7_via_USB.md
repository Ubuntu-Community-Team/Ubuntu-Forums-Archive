---
title: "Connecting to Galaxy Tab 7 via USB"
date: 2012-01-01
forum: General Help
---

### Post by JakartaDean on 2012-01-01
Hi all, I'm hoping someone can help me with a problem.  My wife got a new Galaxy Tab 7 for Christmas, and she very reasonably wants to copy some songs and photos onto it.  I've followed the excellent instructions [here]("http://forum.xda-developers.com/showthread.php?t=1077377").  After rebooting my Tab 10.1 is recognized and mounts automatically.  Hers doesn't; it doesn't even appear in lsusb.  No new device is created under /dev.

Dmesg yields:
[  160.736096] usb 3-1: new full speed USB device using uhci_hcd and address 6
[  160.856164] usb 3-1: device descriptor read/64, error -32
[  161.080141] usb 3-1: device descriptor read/64, error -32
[  161.296125] usb 3-1: new full speed USB device using uhci_hcd and address 7
[  161.416068] usb 3-1: device descriptor read/64, error -32
[  161.640091] usb 3-1: device descriptor read/64, error -32
[  161.856122] usb 3-1: new full speed USB device using uhci_hcd and address 8
[  161.887809] usb 3-1: device descriptor read/8, error -32
[  162.015861] usb 3-1: device descriptor read/8, error -32
[  162.228134] usb 3-1: new full speed USB device using uhci_hcd and address 9
[  162.259979] usb 3-1: device descriptor read/8, error -32
[  162.388036] usb 3-1: device descriptor read/8, error -32
[  162.492108] hub 3-0:1.0: unable to enumerate USB device on port 1

I occasionally, but not repeatably, get errors about device not accepting address 55.  

Those types of errors appear, from Googling, to suggest a USB problem, and the unable-to-enumerate is a long-term issue.  The proposed solution is to disable ehci_hcd slowing down the USB, but I don't want to do that, and it didn't seem to take when I tried to unbind the relevant device.  

My config:  Cheap Chinese netbook running 11.04 ubuntu.  uname -a
Linux prancer 2.6.38-13-generic #53-Ubuntu SMP Mon Nov 28 19:23:39 UTC 2011 i686 i686 i386 GNU/Linux

Does anybody have any ideas?

---

