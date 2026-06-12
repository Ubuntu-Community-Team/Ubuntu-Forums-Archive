---
title: "Failed to load the NVIDIA kernel module"
date: 2011-07-04
forum: General Help
---

### Post by sgbridges on 2011-07-04
This is with a clean install of ubuntu 10.04.  

My machine has 3 monitors, and 2 graphics cards.  I can configure nvidia, and get it to start with two monitors (see x.org.conf.2.screens in the attached zip), but when I try to start with 3 screens (see xorg.conf.not.working) I get a failure (see xOrg.5.log) "Failed to load the NVIDIA kernel module!".

I've gotten 3 screens to work on this machine with 11.04 so it is not a hardware issue.

On startup with 3 screens, the nvidia logo will flash, and the mouse will work for a couple seconds, then everything freezes, and I have to reboot the system.

What do I need to do to fix this.

Thanks.

---

### Post by tigerlxxv on 2011-08-01
I've had the best of luck with NVidia.... and the worst of luck with NVidia... it's still my favorite... Having said that, my problem with 10.04 came in a lot like yours, but with a single monitor. I find that the most recent NVidia package for linux is a little more buggy than what I'd expect. I went to the old version archive on NVidia's website, and just kept going back until I found one that worked. Fortunately for my problem, I only needed to go back by one. Hopefully this helps. If not, post back and we'll see what we can do.

---

### Post by idoitprone on 2011-08-01
If I were to guess, it is the fact that you are now using a much older kernel for your installation. Nutty uses the 2.6.39 while lucid uses 2.6.32. There is around 1 year difference. Nivida compile kernels aganist certain kernel version. 
Try this kernel ppa
[https://launchpad.net/~kernel-ppa/+archive/ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa")

If it does not work, then I do not know

---

