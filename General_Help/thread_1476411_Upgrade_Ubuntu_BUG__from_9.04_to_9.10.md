---
title: "Upgrade Ubuntu BUG  from 9.04 to 9.10"
date: 2010-05-07
forum: General Help
---

### Post by CompUser1 on 2010-05-07
There is a bug in the upgrade from 9.04 to 9.10.  I have repeated it three times.  During the "installing the upgrades" section, the upgrade always stops or freezes in the same place.  The Terminal message stops at "Configuring linux-image-2.6.31-21-generic".
"update-initramfs: Generating /boot/initrd.img-2.6.31-21-generic".  I have a new DELL laptop computer that came with Ubuntu 9.04 pre-installed.  I am using the Update Manager and have previously updated all files for 9.04 before clicking on upgrading to 9.10.

Any help would be appreciated before I send it back to DELL and purchase a Windows operating system that actually works.

---

### Post by Catharsis on 2010-05-07
How long have you let it sit there? It's configuring the kernel; it should take some time.

You can look at your disc activity light for disc usage and have System Monitor open in the background to watch CPU usage. If they're both idle, then the installer has indeed frozen.

---

