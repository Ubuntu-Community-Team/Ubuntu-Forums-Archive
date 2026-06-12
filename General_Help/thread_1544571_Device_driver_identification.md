---
title: "Device driver identification"
date: 2010-08-02
forum: General Help
---

### Post by xefix on 2010-08-02
Hi, everyone

I have a pretty broad question about how devices are identified and assigned drivers in Linux systems. For instance, I have a USB device with some device descriptors (bDeviceClass, bDeviceSubClass, bDeviceProtocol, etc.), which match the descriptors recognized by the driver that this device uses (you can look this information up on LKDDb - linux kernel driver database). My question is on how the matching process is done. Is it coded into the source of the driver itself, somewhere in the kernel, or done entirely with the rules files used by UDEV?

---

