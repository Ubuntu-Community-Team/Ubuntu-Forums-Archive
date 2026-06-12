---
title: "ATI card fan stays on full after resume from suspend. 10.04 LTS"
date: 2011-09-04
forum: General Help
---

### Post by jcntrl on 2011-09-04
As the title suggests, when I suspend or hibernate, then resume, my graphics card fan is on a full speed and will not slow down for anything until I reboot.  All other functions appear to work as normal.

I'm running a homebrew computer: 
Graphics: ATI x1900xtx
MB: ASUS P5WDH
RAM: 2GB

OS: Ubuntu 10.04 LTS

The computer is setup to dual-boot into WIndows XP using GRUB if I choose; the problem does not occur on WIndows XP when I suspend or hibernate from WXP.

I found a bug report on launchpad, but no resolution.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/787540](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/787540)

I can live without suspend/hibernate, but they are handy tools and I'd like to utilise them.

My relative skill level: I can copy/paste things into the terminal and know what 'sudo' means, but generally haven't a clue as to what I'm copying/pasting is doing.

Happy to provide any other needed information to help troubleshoot.

Thanks!
JC

---

### Post by Mark Phelps on 2011-09-05
I'm afraid you're probably stuck with the current situation with that card -- as ATI dropped Linux driver support for that card years ago.  Thus, any fan control options that might ordinarily be included with the Catalyst Control Center (CCC) are NOT available to you -- because there is no ATI driver including CCC that will work with your card and Ubuntu versions newer than 8.10.

---

