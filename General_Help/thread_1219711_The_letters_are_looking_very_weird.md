---
title: "The letters are looking very weird"
date: 2009-07-22
forum: General Help
---

### Post by Vignesh S on 2009-07-22
I have a IBM thinkpad R31,and after installing Ubuntu on it (and even during the installation), I noticed that there were weird grey shadows on some letters. I have no idea what the problem is. It is an inconvenience, and this is the only real glitch that Ubuntu 9.04 is giving me on this laptop. If you don't know what I mean, then the screenshots might help.

---

### Post by ad_267 on 2009-07-22
What video card do you have? Are there any drivers available under System - Administration - Hardware Drivers?

That's a pretty weird problem.

---

### Post by Vignesh S on 2009-07-22
I tried that and unfortunately, there doesn't seem to be any. I'll have a look to see what intergrated graphics chip this ancient thing uses (by computer years anyway)

---

### Post by ad_267 on 2009-07-22
Another random guess at a possible solution would be to play around with the settings under System - Preferences - Appearance - Fonts - Rendering, and the options under "Details".

---

### Post by Vignesh S on 2009-07-23
It is only a temporary fix. It doesn't really work.

The R31 actually uses two i810 G graphics chips, which is accounted for already by the intel xorg driver. But quite obviously, the driver isn't doing its job. Is their any propietry driver options?

---

### Post by ad_267 on 2009-07-23
No the Intel drivers are open source and provided by Intel, so they're installed automatically. I've heard there have been issues with the intel drivers in 9.04 but I haven't been able to find anyone else with this same problem.

This thread may help: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Edit: Found a bug here: [https://bugs.launchpad.net/ubuntu/+source/xfonts-base/+bug/326487](https://bugs.launchpad.net/ubuntu/+source/xfonts-base/+bug/326487)

Looks like you should be able to fix this with a kernel upgrade. I believe there's a kernel PPA you can use to upgrade to the latest kernel. You could also try the Ubuntu 9.10 beta release.

---

### Post by Vignesh S on 2009-07-23
Before I begin doing what it says to do on the intel glitch fixing link you gave me, what is PPA? And how can I access it?

---

### Post by ad_267 on 2009-07-24
PPA means Personal Package Archive, but the [kernel PPA]("https://launchpad.net/~kernel-ppa/+archive/ppa") only seems to have kernels for Intrepid and Hardy.

You can install a new kernel with the packages here instead: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

---

### Post by dtgolder on 2009-09-14
Bump--having the same problem with a Dell X200 laptop, and a fresh install of Jaunty...

Strange thing is that a reboot will fix the problem, but then after the computer is being used more and more letters get the gray (grey?) background....will continue to search for a solution.

---

### Post by Vignesh S on 2009-09-17
Yep, the kernel upgrade helped a LOT. The letters stopped going crazy. Sure, there were still problems, but it was definately not as bad as it was beforehand. If there were still problems, I would go into the Text Font changing thing i.e. Right clicking in the desktop, clicking on change background, then changing the tab at the top to fonts. 

But even this became too much for me, and I upgraded to 9.10. But the price I pay for that now is constant crashes, and Blueman not working :-(.

Try sticking to 8.10 or 8.04. Heard that they worked without any problems. Only I can't because they won't even load up, even the Live CD option doesn't. :-(

---

