---
title: "Automatically login to console"
date: 2010-08-21
forum: General Help
---

### Post by Random_Net on 2010-08-21
Hi,

Is there anyway I can automatically login to console without having to provide username and password as soon as I boot into the machine?

---

### Post by sisco311 on 2010-08-21
> **Random_Net said:**
> Hi,

Is there anyway I can automatically login to console without having to provide username and password as soon as I boot into the machine?

Yes, install mingetty. Then edit /etc/init/tty**X**.conf (where **X** is the number of the virtual console) to something like:

```
# tty**1** - getty
#
# This service maintains a getty on tty**1** from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/mingetty --autologin USERNAME tty**1** linux

```

---

### Post by yaztromo on 2010-09-27
If you want "mingetty --autologin username tty1" to work in lucid you have to disable the plymouth boot logo by removing quiet and splash from the kernel options in /etc/default/grub then run sudo update-grub

I spent ages trying to get it to work today until I tried this.

---

