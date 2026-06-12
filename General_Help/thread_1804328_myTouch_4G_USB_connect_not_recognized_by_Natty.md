---
title: "myTouch 4G USB connect not recognized by Natty"
date: 2011-07-14
forum: General Help
---

### Post by gimpgyn on 2011-07-14
Natty does not see my phone.  The phone is configured as a disk drive, as it should be.  I've tried enabling and disabling USB debugging on the phone as well.

The kernel sees it.  lsusb displays the USB "bus 003 device 003" and the ID "High Tech Computer Corp."

It is also listed in the dmesg file "usb 3-3: new high speed USB device using ehci_hcd and address 2".

But when I cat /dev there are no sym links from the sdd devices, which I understand should be created if recongnized by the system.  It is no listed in the /proc/bus/input/devices file.

I'm new to this and would like a better understanding of how to troubleshoot the problem and what the sequence and requirements are for "seeing" my phone as a file system.

Any suggestions?

Am I asking too much?  Any technical experts out there? Help!!!

---

