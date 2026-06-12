---
title: "Digital Prism 3 in 1 Photo converter"
date: 2012-03-14
forum: General Help
---

### Post by howellb3383 on 2012-03-14
Hi there. So, I was able to get a photos, negatives, and slides scanner for a really great price. Though I was concerned that Ubuntu wouldn't pick up the device. Now at the house, plugged in, those fears were valid. I have looked online to see if there were any drivers for Linux, yet, none found. Also, the company doesn't have a website. I was wondering if anyone could help in getting it to work. 

Just so everyone has an idea of the product, here it is on Amazon: [http://www.amazon.com/3-IN-1-PHOTO-CONVERTER/dp/B004LBBLYI](http://www.amazon.com/3-IN-1-PHOTO-CONVERTER/dp/B004LBBLYI)

In advance, thank you for any, and all help.

System Specs: 

Compaq Laptop
3Gb Memory
250Gb HDD
64Bit Ubuntu 11.10

---

### Post by ajgreeny on 2012-03-14
Assuming at is attached by usb, what does ```
lsusb
``` in terminal report, if anything.  It may give some indication of what action or driver is needed.

Have you also tried running ```
sane-find-scanner
```with it attached to see if it is recognised by sane.

---

### Post by howellb3383 on 2012-03-14
Yes it is connected via USB. The lsusb looks as such:
 
Code:
~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05a9:1550 OmniVision Technologies, Inc. VEHO Filmscanner

The sane-find-scanner command read:

Code:
~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x05a9, product=0x1550) at libusb:001:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

---

### Post by ajgreeny on 2012-03-14
Looks like sane has found the scanner, 
```
Bus 001 Device 005: ID 05a9:1550 OmniVision Technologies, Inc. VEHO Filmscanner
found USB scanner (vendor=0x05a9, product=0x1550) at libusb:001:005
```so install xsane and run it to see if the scanner works or not.

I am not sure what you want to do with it, but I doubt that any software that came with it will work in Ubuntu, though you might try it in wine, however, if the scanner part works there are plenty of packages for ubuntu that can convert images in many different ways.

---

### Post by gordintoronto on 2012-03-15
On the same page on Amazon, there is a Wolverine device to do the same job. It scans onto a memory card, and then you plug the memory card into your computer. No software or drivers to worry about, "it just works."

---

