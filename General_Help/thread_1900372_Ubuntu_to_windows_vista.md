---
title: "Ubuntu to windows vista"
date: 2011-12-26
forum: General Help
---

### Post by Rogzilla on 2011-12-26
Hey, 

I got a new laptop for xmas off the family and promised this one to the father in law. However he can bairly turn a laptop on nevermind use a Linux based OS.

I'm trying to go back to windows vista but struggling, from not having the correct boot format to something missing on boot disks I just cant seem to get it going. 

Is there any kind of tutorial or am I doing it completely the wrong way? I've been booting from windows CD and trying to install it from there. I've tried deleting partitions and just killed ubuntu so I had to reinstall it (which was np at all btw)

Help is greatly appreciated :)

---

### Post by Mark Phelps on 2011-12-26
First of all, let's get our terms straight ... Vista comes on a DVD, not on a CD.  So, if what you have is really a CD, then it's unlikely that you will be able to install Vista with it -- as the CDs are most generally Restore media and all they do is launch an app that restores a PC that originally came with Vista on it -- presuming the Recovery partition is still intact.

If you have a DVD (and just called it a CD), then you should be able to install Vista from that -- but you will need an activation code.  IF the PC came with Vista on it, there should be a sticker on the PC with the code you will need.

If you boot from the DVD and the installer won't install, it's likely the presence of a Linux filesystem is confusing it; in that case, you will need to boot from an Ubuntu LiveCD and use the Disk Utility to remove the Linux partitions.

Then, reboot from the Vista DVD -- and installation should go OK.

---

