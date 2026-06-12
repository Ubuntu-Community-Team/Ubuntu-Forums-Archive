---
title: "Possible downgrade kernel 2.6.28-11 to 2.6.22?"
date: 2009-11-05
forum: General Help
---

### Post by wulfgang on 2009-11-05
Hello, I was wondering if it was possible to downgrade from 2.6.28-11 to 2.6.22 in ubuntu 9.04.
See I'm trying to get my bluetooth headset to work, but there is a bug in kernel 2.6.24, and in 2.6.28.
( [Bug #222922]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/222922"))
Any help much appreciated.
Thanks.;)

---

### Post by sgosnell on 2009-11-05
You can get all the kernels [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/) as .deb files.  Download the one you want and install it with gdebi.  You will probably have to manually select it at boot, because grub sets the latest version as default, but it's not a big problem.  If you really want to get rid of the later kernels, you can boot into the older one and remove them with Synaptic.  I would suggest making sure the older one works well before removing anything, though.  You can have as many kernels installed as you want, and choose between them at boot time.

---

### Post by wulfgang on 2009-11-05
> You can get all the kernels [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") as .deb files. Download the one you want and install it with gdebi. You will probably have to manually select it at boot, because grub sets the latest version as default, but it's not a big problem. If you really want to get rid of the later kernels, you can boot into the older one and remove them with Synaptic. I would suggest making sure the older one works well before removing anything, though. You can have as many kernels installed as you want, and choose between them at boot time. 
Thanks!! I'm going to bookmark that link. :)

---

