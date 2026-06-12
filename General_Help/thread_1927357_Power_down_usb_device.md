---
title: "Power down usb device"
date: 2012-02-17
forum: General Help
---

### Post by colonelpenguinx on 2012-02-17
I would like to be able to power down my usb devices and then power them back up in ubuntu 11.1 64bit.  I need to do this because the module for the attached device doesn't load properly during bootup.  I can get the devices working by manually unplugging the devices, rmmod ing the module, and plugging them back in.  I do not want to have to keep unplugging the devices after reboot.  Thanks in advance.

---

### Post by Bobhuber on 2012-02-17
> **colonelpenguin said:**
> I would like to be able to power down my usb devices and then power them back up in ubuntu 11.1 64bit.  I need to do this because the module for the attached device doesn't load properly during bootup.  I can get the devices working by manually unplugging the devices, rmmod ing the module, and plugging them back in.  I do not want to have to keep unplugging the devices after reboot.  Thanks in advance.
Did you try loading the module in /etc/rc.local during boot ?

---

### Post by colonelpenguinx on 2012-02-17
Yes... I have tried this.  This the module is loading on its own, but it takes so long that it doesn't load on all of the devices.  It is multiple HVR-850 tv tuners that I am trying to get working.  It will load for one device, but not both.  Unplugging, rmmod ing, and repluggin the devices is all that has worked so far, but it I would like to come up with a scriptable solution.

---

### Post by colonelpenguinx on 2012-02-22
Bump?  Anyone able to advise on how to power down and power back up usb ports with a script?

---

