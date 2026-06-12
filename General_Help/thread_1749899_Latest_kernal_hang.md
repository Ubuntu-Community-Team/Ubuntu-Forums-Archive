---
title: "Latest kernal hang"
date: 2011-05-05
forum: General Help
---

### Post by warlocklw on 2011-05-05
I updated ubuntu kernal to latest one, forgot the numbers already. When I restart, it hangs while loading kernal. I usually can choose which kernal to load, but now the 'choosing page' can't even load already. Pls help.

---

### Post by fdm on 2011-05-05
That sounds more like a grub problem to me, but I could be wrong.

Throw in your install cd, and boot up in rescue mode. This will land you at a root shell. Run "uname -r" and record your kernel version. Use "apt-get remove linux-image-X.X.XX-XX-generic"(with the Xs replaced with the version numbers).

To install different kernels, run "apt-cache search linux-image" to find the kernels available, and use apt-get install to grab the older one you want. You might have to configure your /etc/network/interfaces to connect to the internet.

If that does not help, try removing grub-pc and grub-common and installing grub(or grab directions for restoring grub2 from the forum).

---

