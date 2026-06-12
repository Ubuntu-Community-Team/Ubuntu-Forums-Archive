---
title: "USB Mass Storage Device not recognised"
date: 2009-11-18
forum: General Help
---

### Post by lautarox on 2009-11-18
I've upgraded my Ubuntu version from 9.04 to 9.10, I had experienced some problems with python-expect and I've reinstalled it and configured it successfully. My problem is that with this upgrade I haven't been able to use my pen drive again, it doesn't recognize it anymore. I've searched to find a solution to my problem but I can't find one.
Thanks in advance.

---

### Post by peakshysteria on 2009-11-18
Have you Rebooted your box? Had the same problem even though the output of lsusb in terminal listed all devices. Wouldn't recognize any USB thingies at all. Ran the latest updates and rebooted. Est voila; all is happy days once again. Give it a shot. Sometimes the simplest solution is the right thing :)

---

### Post by lautarox on 2009-11-18
Thanks for your answer. Yeah, the problem has been bothering for a while, I've rebooted it and shuted it down..

---

### Post by peakshysteria on 2009-11-18
Open a terminal --> Do you find your device with:
```
lsusb
```

---

### Post by lautarox on 2009-11-18
Well.. I also have a printer and a camera connected and it doesn't show anything at all.

---

### Post by fatmystic on 2009-11-18
Thanks peakshysteria.

The lsusb -l does not show anything. The computer had been tried with shutdown and boot u-p cycles. The USB drives had been pulled in and out while the ubuntu is booted as well as USB had been inserted at the power on. There is no USB device is detected.

The ls -al /dev/bus/usb is empty. So as ls usb.

---

### Post by lautarox on 2009-11-18
Do you have the same problem? Take a look here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455408](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455408) .
I tried downgrading usb utilities but it didn't work neither, I think it's a kernel's problem..

---

### Post by fatmystic on 2009-11-18
Thanks lautarox,

Looks like the similar end of the bug. However the bug/455408 is on instability of USB devices and downgrading the USB driver. And the bug has not been resolved. 

I have ubuntu9.04 disk and I will try booting on the computer to see if it detects tne USB. I am not planning to load the HD until the resolution is found.

---

### Post by fatmystic on 2009-11-19
Confirmed that ubuntu 9.04 CD acts same as ubuntu 10.4. That is USB device is not detected. As mentioned in the bug/455408, it is the kernel bug. I am not sure when it was introduced.

Just my thinking....

---

