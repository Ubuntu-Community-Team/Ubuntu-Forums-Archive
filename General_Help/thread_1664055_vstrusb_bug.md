---
title: "vstrusb bug"
date: 2011-01-10
forum: General Help
---

### Post by Carharttjimmy on 2011-01-10
Hi,

I'm using  2.6.32-27-generic #49-Ubuntu SMP on a 64 bit machine.
The kernel module vstusb is interfering with libusb when trying to access
a USB device with Vendor ID 0x2457 and Product ID 0x1022.  Do you know any reason
why vstusb would try to take control of this device.  It is a spectrophotmeter and not a 
MAC floppy drive.  I'm not sure who is the kernel maintainer of vstusb or who else to
contact.  My quick fix is to remove the offending kernel module, but I need to do this for
every update of the kernel.

---

