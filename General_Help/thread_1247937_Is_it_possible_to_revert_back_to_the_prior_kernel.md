---
title: "Is it possible to revert back to the prior kernel?"
date: 2009-08-23
forum: General Help
---

### Post by cptrohn on 2009-08-23
I have a device that is not yet supported in the new kernel and I was wondering if it is possible to revert back to the earlier kernel?

---

### Post by michy99 on 2009-08-23
You should have a choice in your Grub menu to use the previous kernal.

---

### Post by drs305 on 2009-08-23
If you don't see the previous kernel in your menu.lst, but you haven't uninstalled it, install StartUp-Manager and go to the Advanced tab. Set the "Limit Number of Kernels to Keep" to 2 or more and you should see the older kernels. You can also set the default kernel on the Boot Options tab.

For information on StartupManager, how to install, tips, etc. click on the "SUM" link in my signature line.

---

### Post by tgalati4 on 2009-08-23
Unless it was a minor upgrade to linux:

vmlinuz-2.6.28-11-generic  

This could refer to any version of 2.6.28-11 (which I'm currently running 2.6.28.11.15).

You can boot into any kernel that exists in /boot

ls /boot/vmlinuz*

If you can't find an earlier kernel in the repositories, you may be able to simply copy it from the Live CD.  You will have to remake your initrd.img using dpkg-reconfigure.

---

### Post by michy99 on 2009-08-23
> **tgalati4 said:**
> Unless it was a minor upgrade to linux:

vmlinuz-2.6.28-11-generic  

This could refer to any version of 2.6.28-11 (which I'm currently running 2.6.28.11.15).

You can boot into any kernel that exists in /boot

ls /boot/vmlinuz*

If you can't find an earlier kernel in the repositories, you may be able to simply copy it from the Live CD.  You will have to remake your initrd.img using dpkg-reconfigure.

The kernals that have been installed so far in Jaunty are 2.6.28-11, 2.6.28-13, 2.6.28-14, and 2.6.28-15

---

### Post by tgalati4 on 2009-08-23
Jaunty shipped with 2.6.28.11.15 and now 2.6.25.15.20 is currently available.  I don't know how you can load the intermediate kernels if you didn't upgrade them previously.

---

### Post by drs305 on 2009-08-23
> **tgalati4 said:**
> Jaunty shipped with 2.6.28.11.15 and now 2.6.25.15.20 is currently available.  I don't know how you can load the intermediate kernels if you didn't upgrade them previously.

You can just go into synaptic and select the "linux-image-2.6.28-XX" kernel you wish. Also install the associated linux-header. The kernels will be installed but not put in use unless you change your menu.lst.

To update the menu.lst, run "sudo update-grub", which should then display the additional kernel(s) in the menu.

---

