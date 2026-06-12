---
title: "Use uhci_hcd driver for HotPluggin USB Mouse devices"
date: 2011-10-12
forum: General Help
---

### Post by theslightestofhand on 2011-10-12
Hi,

I have an Dell Latitude E6510 with Ubuntu 11.04 and I am having issues with my USB mouse lagging horribly.  I do not have this issue on my Dell Precision desktop.  

The only difference I can see through dmesg and Xorg.O.log logs is that the usb driver used on my laptop is ehci_hcd while my desktop uses uhci_hcd.  

I would like to test this difference to determine if ehci_hcd is the issue.  Is there anyway associate my USB mouse device to use uhci_hcd and not ehci_hcd?  xorg.conf.d does not allow me to set the usb driver used for the mouse device.  

Thanks,

J

---

### Post by theslightestofhand on 2011-10-13
Just plugged in my mouse this morning to try to debug some more and it seems to work.  Other threads exist on this issue of intermittent mouse lag after reboots on E6510.  I'll will poke around in those threads.

Mod can close or delete this thread.

---

