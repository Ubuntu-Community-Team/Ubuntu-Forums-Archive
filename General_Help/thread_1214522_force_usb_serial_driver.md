---
title: "force usb serial driver"
date: 2009-07-16
forum: General Help
---

### Post by dread22 on 2009-07-16
I have a CP210X usb serial device with a weird identifier which is not being recognized. I have the CP210X driver module on my system but the device is not being assigned to it. Is there some way that I can force it to use the driver?

---

### Post by dread22 on 2009-07-19
Nevermind. I just recompiled the kernel adding the device identifier to the cp2101 driver code.

---

