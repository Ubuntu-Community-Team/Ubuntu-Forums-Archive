---
title: "Question ABout Drivers"
date: 2011-03-29
forum: General Help
---

### Post by LonelyAspie on 2011-03-29
If I install Linux (Ubuntu, OpenSuse, Mint etc) on one computer and takke the HDD out and hook it up to another computer, will it automatically install the drivers, like it does during installing? The reason I ask, is because I have a few HDD's laying around and I like tto try out different distros, and if I find one that that I like, I want to install it in another computer for someone to try out, without having to reinstall it again.

---

### Post by deathadder on 2011-03-29
The amount of success you get depends on the hardware differences between the machines. Most of the "userfriendly" distro's use some form of udev rules to determine what modules to load during boot (I believe!). So you should be ok, to a extent, you may get some problems if you install specific drivers (I'm thinking nVidia / ATI). 

Normally it's not a recommended thing to do, but as long as you're not going from 32-64 bit or from sparc to intel based you should be able to boot at least...

---

### Post by anglican on 2011-03-29
> **LonelyAspie said:**
> If I install Linux (Ubuntu, OpenSuse, Mint etc) on one computer and takke the HDD out and hook it up to another computer, will it automatically install the drivers, like it does during installing? The reason I ask, is because I have a few HDD's laying around and I like tto try out different distros, and if I find one that that I like, I want to install it in another computer for someone to try out, without having to reinstall it again.A problem that you may run into is that the initrd.img may be incorrect on the new computer preventing the OS booting. If this happens (you'll get a message about being unable to mount the root filesystem) you can boot from a live cd, chroot to the hard-disk and run update-initramfs to create a usable initrd.img. Otherwise Ubuntu is pretty good at detecting hardware and re-configuring.

H

---

### Post by rgb1701 on 2011-03-29
> **anglican said:**
> A problem that you may run into is that the initrd.img may be incorrect on the new computer preventing the OS booting. If this happens (you'll get a message about being unable to mount the root filesystem) you can boot from a live cd, chroot to the hard-disk and run update-initramfs to create a usable initrd.img. Otherwise Ubuntu is pretty good at detecting hardware and re-configuring.

H

In most cases, swapping a hard drive to a different machine Just Works for me.  This is yet another big technical strength of Ubuntu/linux vs Windows, which requires new drivers to be installed for all the hardware differences, plus the authentication/WGA nonsense that locks a Windows load to the motherboard/hard drive combo.

As another post mentioned, the vide driver may be the only issue.  Just be sure to disable (de-activate) the ATI or Nvidia driver in System>Administration>Hardware Drivers, reboot on the original machine to a usable desktop, then remove the harddrive.  Re-activate the appropriate video driver on the target machine.

---

