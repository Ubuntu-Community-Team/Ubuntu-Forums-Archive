---
title: "New DVD drive not recognized by Ubuntu 10.04"
date: 2011-01-17
forum: General Help
---

### Post by DrScum on 2011-01-17
I had a broken DVD-drive on a Dell Inspiron 6400 Laptop. After replacing it with another brand it's recognized by the bios but is no longer active after booting to Ubuntu 10.04.
I guess I need to tell the OS that it has a different type drive and thus has to load a different set of drivers. How do I do this?

---

### Post by lithopsian on 2011-01-17
Possibly, but normally you should be able to swap devices and they will be recognised automatically for what they are.  A lot of effort has gone into things like udev that correctly detect your hardware each time you boot and load the correct drivers.  Take a look in /var/log/dmesg and see what it says about your CD drive.

---

### Post by DrScum on 2011-01-17
The device is not listed in the dmsg log neither is it listed in the lshw output.

The drive doesn't react at all, after the OS is loaded. During the boot process it works as it should, i.e. I can eject it and the diode flashes. As soon as the OS is loaded it's completely dead.

---

