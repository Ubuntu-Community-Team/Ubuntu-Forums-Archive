---
title: "Removing an old Kernel."
date: 2012-01-04
forum: General Help
---

### Post by emptycoder on 2012-01-04
I have upgraded my system (Ubuntu 11.10 x64) and now I have two Kernels on the GRUB Screen, new one 3.0.0.14 with old one 3.0.0.12.
I was searching for a guide to show how safely remove old Kernel because I don't need it, I came across to this website

[http://connectwww.com/how-to-remove-old-linux-kernels-in-ubuntu-via-synaptic-package-manager/614/](http://connectwww.com/how-to-remove-old-linux-kernels-in-ubuntu-via-synaptic-package-manager/614/)

It says that I can remove it via synaptic package manager, all I have to do is search for the kernel by typing Linux-image on the quick search field, find the old one with green selection boxes (showing currently installed) and right click then choose mark for complete removal.
I'm just confused with something here.
I have found so many other images, like linux-image-3.0.0-12-virtual, linux-image-3.0.0-13-server, linux-image-3.0.0-12-vir and many other images.
I'm not an expert and I don't want miss with anything, is it safe to remove the old one by just selecting linux image (linux-image-3.0.0-12-generic 3.0.0-12.20 )with green box and choose mark for complete like that guide said?
Thanks.

---

### Post by QIII on 2012-01-04
I generally keep the previous kernel as a backup in case something blows up the current one.

It takes just a bit of space on the disk.

There is no rush to get rid of it.  When you get a newer kernel in a future update, use Synaptic to remove .12

In Fedora you can run a utility from the console that will find and delete old kernels -- except for the most recent previous one if you use the default flags.  It seems that the Fedora developers think that keeping one kernel back is a wise idea, too.

---

### Post by Lars Noodén on 2012-01-04
Yes, you can safely remove the old one if you successfully booted with the new one.  The reason the old ones are around is so that if the new kernel fails to work, you can fall back to the old one and still boot.

You will also have to get rid of the older linux-headers-* packages.  Autoremove should get them after you've removed the old kernels.

---

### Post by drs305 on 2012-01-04
Here's a thread I wrote about it. I too recommend keeping at least one older working kernel, and highly recommend using Ubuntu Tweak to remove older ones.

[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by emptycoder on 2012-01-04
Thanks everyone, that was helpful.
I will mark this thread as SOLVED.
Thanks again.

---

