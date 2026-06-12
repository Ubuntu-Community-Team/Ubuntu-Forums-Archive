---
title: "Wubi install - can I patch and rebuild Natty kernel for flapjack KVM switch"
date: 2011-06-15
forum: General Help
---

### Post by meggiedude on 2011-06-15
Hi,

I have a Belkin Switch2 KVM switch that I have using successfully in W£nd%ws for some time
Quite often (like, most times) though the wireless switcher does not work and I have loaded a Belkin utility called 'flip' to allow me to switch between my home desktop and my work laptop.
There is no Linux version of this. However some clever bod has created a utility called flapjack (version 0.3) which supposedly does the job for Linux.
[http://linux.softpedia.com/get/System/Hardware/flapjack-25860.shtml](http://linux.softpedia.com/get/System/Hardware/flapjack-25860.shtml)

I have ran configure, make and make install.
The instructions then tell me to do the following:
> cp doc/flapjack-kernel-2.6.20.4.patch /tmp
(root)# cd /usr/src/linux
(root)# patch -p1 </tmp/flapjack-kernel-2.6.20.4.patch

Replace the "/usr/src/linux" with the location of your linux source
code. After applying the patch, rebuild and reinstall the kernel and
reboot or reload the usbhid module.
So can I do this with a wubi install and (as a newbie) how do  rebuild and install the kernel. Is it even possible without compromising what is a Wubi install, not a 'proper' build.

Cheers,

MD

---

