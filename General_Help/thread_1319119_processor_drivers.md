---
title: "processor drivers"
date: 2009-11-08
forum: General Help
---

### Post by vikman on 2009-11-08
New to linux. Installed ubuntu 9.10 . It automatically found drivers for my wifi and I was able to install the video driver -FGLRX.
when I go to system->hardware drivers it shows only those 2 drivers as being installed. What about other drivers?- how do I get a driver for my turion x2? Is it already preloaded and I just cannot see it?

---

### Post by hal10000 on 2009-11-08
SYSTEM--->HARDWARE DRIVERS shows only proprietary drivers which can be **installed**.

If you want to see all your hardware drivers and inventory use "Hardware viewing" (Device Manager) or, if you are on the command line
```
sudo lshw
```

The driver for your cpu is built into the linux kernel, otherwise your system would be unusable.

---

