---
title: "Kernel 2.4 Installation Failure"
date: 2006-06-27
forum: General Help
---

### Post by afoglia on 2006-06-27
I'm trying to install kernel-image-2.4.27 in hopes that it will fix a wireless problem, but the default configuration is causing a kernel-panic upon loading.

I installed kernel-image-2.4.27-2-686 and cramfsprogs and initrd-tools, and kernel-pcmcia-modules.  Upon installation and reboot, after uncompressing the kernel, I get the error:
Kernel panic: VFS: Unable to mount root fs on 03:02

I then tried the pcmcia-modules package, and it too caused the same error.  When I try to dpkg-reconfigure the kernel to rebuild the initrd image, I see this error (irregardless of which of the two modules packages I've installed):
depmod: *** Unresolved symbols in /lib/modules/2.4.27-2-686/kernel/drivers/net/wireless/orinoco.o
depmod: *** Unresolved symbols in /lib/modules/2.4.27-2-686/fs/xfs/xfs.o
W: kernel 2.4.27-2-686 too old for initramfs on i386
W: not generating requested initramfs for kernel 2.4.27-2-686

These same errors appear when the kernel-pcmcia-modules package is reconfigured as well.  (But not the pcmcia-modules package, but they are probably hidden behind the terminal's questions.)

What's the next step?

---

### Post by patrickfromspain on 2006-06-27
You can't install a 2.4 kernel in dapper. I don't know why it's in the repos though.

For your wireless problems.. maybe you could open a thread and ask for specific help.

---

### Post by afoglia on 2006-06-27
> You can't install a 2.4 kernel in dapper. I don't know why it's in the repos though.

What's the issue?  What if I were to compile it myself?

I did get the Debian Sarge 2.4.27-3 kernel-image and kernel-pcmcia-modules packages to install and booted from them, but both the pcmcia modules and X server failed.

> For your wireless problems.. maybe you could open a thread and ask for specific help.

I did that Saturday and there's been no response. [http://www.ubuntuforums.org/showthread.php?t=202148](http://www.ubuntuforums.org/showthread.php?t=202148)

My mistake might be tagging it as xubuntu when it obviously has nothing to do with my desktop environment.

---

### Post by -deadcats on 2006-06-27
I think you'll find that the 2.4 kernel is incompatible with a large number of wireless hardware. The 2.6 kernel has better support.

regards,
-dc

---

### Post by afoglia on 2006-06-27
> I think you'll find that the 2.4 kernel is incompatible with a large number of wireless hardware. The 2.6 kernel has better support.

I have an Orinoco card which had good Linux support when I first got it many years ago.  Plus, I know it works with 2.4, because I'm running Debian Sarge with the 2.4 kernel on another laptop, and the card is working perfectly in that system.

The idea was that if I could get 2.4 running in Ubuntu, I could determine whether it was a Linux kernel problem, or an Ubuntu problem.  (I doubt it's my configuration, because, as I wrote in the post I linked to above, booting from the net-install floppies, I am unable to see the new router, but I was able to see the old one.)

---

### Post by -deadcats on 2006-06-27
[QUOTE=afoglia]...booting from the net-install floppies, I am unable to see the new router, but I was able to see the old one.)[/QUOTE]

Please, tell us more...

regards,
-dc

---

### Post by afoglia on 2006-07-06
(Sorry, didn't notice any e-mail notification.)

Well, as I explained in the other thread, we recently got a new router.  The old was 802.11b, the new is a Belkin 802.11b/g/pre-N.  My ubuntu laptop no longer connects to the router.  I've repeatedly tried iwconfig to no avail.  The card is an Orinoco Classic Gold PCMCIA card.  My debian stable laptop (which is the one running the 2.4 kernel) connects fine with the same card, and the ubuntu laptop connects fine when I boot off the Windows partition.

I also cannot connect to the wireless g router at work, which I believe is a Linksys model.  Perhaps also pre-N, as it's likely very new.

Oddly, just last weekend I took my Ubuntu laptop to the local coffeeshop where I was able to get onto their 802.11b/g router.

This happened in both breezy and dapper.

---

