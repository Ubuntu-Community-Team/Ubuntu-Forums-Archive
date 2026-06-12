---
title: "No graphic mode after kernel update"
date: 2009-11-26
forum: General Help
---

### Post by cristian.vrabie on 2009-11-26
Hey guys.
I had Ubuntu 9.10 perfectly working with kernel 2.6.31-14-generic with the latest drivers from their website (x86-190.42). 
At some point I tried to install 2.6.31-14-pae because i have 4G of Ram. I followed the procedure that worked on Ubuntu 9.04 and it got installed, however, when booting in 14-pae i would get a console and the display kept flickering (like once every second). The input also seemed to be affected. If I typed something during a "flicker" that key would not get processed and i would have to type it again. 
I gave up at that time because I had no time to investigate and uninstalled 14-pae. Yesterday (I think), there was an update to kernel 2.6.31-15-generic. It seems this kernel behaves exactly as the pae kernel. 
Do you have any idea what might cause this? I would hate to get stuck on kernel 14.
Thanks,
Cristian

---

### Post by bumanie on 2009-11-26
Whenever you use gpu drivers from the nvidia website, at each kernel upgrade, you need to reinstall the drivers. I suggest you boot in to recovery mode and try to fix things from there by using the ubuntu drivers which will update with a kernel upgrade. Alternatively, you can use wget to get the drivers from the nvidia site, but I am not 100% sure of the syntax.

---

### Post by ene_dene on 2009-11-26
You need to install nvidia drivers for every kernel upgrade.
You don't need a special kernel for 4Gbs of RAM.

But if you use it anyway, you need to find old xorg.conf which doesn't contain nvidia drivers in it (in /etc/X11/) and put it instead the xorg.conf you have now, and the system will load, then you can install new nvidia drivers.
Or try to get to console by trying some esc pressing during boot process (it's really not clear how can you get to single user mode in 9.10, grub is bugy), and install the nvidia drivers then.

---

### Post by cristian.vrabie on 2009-11-26
I wasn't aware that the 3rd party drivers need to be reinstalled. Thank you very much for your help! This solved my problem.

---

### Post by ene_dene on 2009-11-26
> **cristian.vrabie said:**
> I wasn't aware that the 3rd party drivers need to be reinstalled. Thank you very much for your help! This solved my problem.
If you want to avoid reinstalling the drivers I suggest that you lock kernel version so it doesn't get upgraded. Find it in synaptic and then go to package menu and select lock package version. Of course that means that you will not get the security updates for kernel but in most cases for desktop system it's not essential.

---

