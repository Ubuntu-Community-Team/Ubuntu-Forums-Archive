---
title: "Update Headers and Broadcom Driver"
date: 2010-03-04
forum: General Help
---

### Post by jose1986 on 2010-03-04
So these are my directions, how do I get the current version of my linux headers?  I do not have wireless internet on my laptop, so I need to know what the current version is before installing them.


> - Go on wired network.
- Install corresponding kernel headers.
$ sudo aptitude install linux-headers-$(uname -r)
- Install the driver.
$ sudo aptitude install bcmwl-kernel-source
- If you already have it installed, you may need reconfigure it.
$ sudo dpkg-reconfigure bcmwl-kernel-source
- Activate the driver under*System*>*Administration*>*Hardware Drivers.

---

