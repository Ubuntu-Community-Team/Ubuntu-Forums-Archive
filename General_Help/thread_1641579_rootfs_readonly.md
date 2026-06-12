---
title: "rootfs readonly"
date: 2010-12-09
forum: General Help
---

### Post by SimaHWT on 2010-12-09
Hello,

I need to have my system in readonly mode, to prevent any filesystem error if the machine poweroff.

I still need to have /dev and /var on r/w mode for the system to work.

What is the best way to tell the init scripts to mount / ro and to mount /var and /dev rw (with 2 different partitions of course) ?

I managed to do this on another distro, but I'm not familiar with ubuntu boot process and I don't know where is the best place to do that.

Using fstab is not possible (it won't mount / and /var).

Sima.

---

