---
title: "usb 3.0 PCIe card recommendations"
date: 2012-04-09
forum: General Help
---

### Post by linuxcss on 2012-04-09
anybody have recommendation for a PCIe USB 3.0 card that works well with ubuntu 11.10?

I like to see near 100Mbytes/secs copy from external USB 3.0 hard drive to an internal drive.

---

### Post by linuxcss on 2012-04-11
tested 2 different USB 3.0 PCIe cards but ONLY see read at 47 megabytes a second from a usb 3.0 hard drive to an internal sata drive

might this be some driver concern in xubuntu 11.10?

i get this from 
dmesg | grep Super
[   33.919422] usb 9-1: new SuperSpeed USB device number 2 using xhci_hcd
[   47.875447] usb 9-2: new SuperSpeed USB device number 3 using xhci_hcd

something else to check or verify?

---

