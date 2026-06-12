---
title: "Xen- Ubuntu kernel mystery"
date: 2005-02-03
forum: General Help
---

### Post by TravisNewman on 2005-02-03
OK You may have read in other threads that I've been trying to get Xen going. It hasn't been easy, and that's in part because of the Ubuntu kernel, or in the way the system interacts with the kernel. 

Basically, the way Xen works is that Grub loads Xen as the kernel, and then the Xen kernel loads the standard vmlinuz type kernel (called vmlinuz-xxx-xen0, since it's virtual domain 0). All subsequent virtual domains are loaded by the xen daemon through dom0. So...

In order to get it going, you first have to compile the kernel with ARCH=xen since you're technically not running i386 anymore. I got the kernel to compile, and the xen kernel loaded it just fine, only when I booted into Ubuntu, I had no sound, and there was either no support for /dev/hdb or there was no support for the fat filesystem.

I have been emailing back and forth with one of the Xen developers, and he's sent me a .config to try out, and even posted a kernel he compiled for me to download. THEN it occurred to him to try compiling the kernel from the vanilla kernel source (no custom patches) without ARCH=xen. And sure enough, that didn't work either. I tried compiling a vanilla kernel with the .config that ships with the Ubuntu kernel, and this didn't work. BUT compiling the Ubuntu kernel tree with either .config worked fine. Unfortunately, the Ubuntu kernel patches only affect the architectures it supports (i386, ppc, AMD64, etc), so using the Ubuntu kernel tree to build a Xen kernel doesn't work.

I even installed Fedora and used their rpms, and got Ubuntu to boot with the Fedora Xen kernel, and it acted exactly the same-- no hdb1 partition, and no sound-- though they both worked perfectly fine in Fedora.

SO. There's something disturbing about the way Ubuntu interacts with the kernel, since custom kernels not built off of the Ubuntu kernel tree don't work with certain things.

Does anyone know what might be causing this, how to get around it, or how to fix it?

---

### Post by TravisNewman on 2005-02-04
I should point out that I'm using Hoary, but I don't really think that has anything to do with it, though I could be wrong.

Also, if anyone could explain how to use this:
[http://thread.gmane.org/gmane.comp.emulators.xen.devel/5846](http://thread.gmane.org/gmane.comp.emulators.xen.devel/5846)
to make the debs for xen (which are soon to hit the debian repos, but in Debian terms, who knows what soon means?)

---

### Post by az on 2005-02-04
My one cent since I am not even smart enough to have two:

Ubuntu uses alsa for sound.  You you have the alsa source with your vanilla kernel?

Does the Fedora kernel use an initrd?  I'd guess that it does. How did you build it?  Did you use debian/Ubuntu intrd tools?  Would this be a place to look for the vfat hdb funnyness?

---

### Post by TravisNewman on 2005-02-04
Aw, no more shatner!

Anyway, no I don't have the alsa source with the vanilla kernel-- I did a menuconfig and selected ALSA support-- I didn't know I needed the ALSA source. This is the first time I've ever compiled from vanilla.

Yeah the Fedora kernel does have an initrd, and it seemed to make it when it was installed. But the ubuntu kernel that I compiled off of the custom config didn't, and hdb worked. I've never actually used initrds when I made custom kernels-- are they really needed?

---

