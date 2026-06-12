---
title: "Looking For A Push In The Right Direction!"
date: 2010-07-09
forum: General Help
---

### Post by chaz7201 on 2010-07-09
Hey All, Im new to this Ubuntu! And am absolutely loving it! I have a m2n32-SLI board and a Nvidia 7900gs and I am absolutely amazed at what this machine is capable of on a fresh install! over 700fps even with compiz all running and streaming video - unstopable! im glowing!:popcorn:

My interest now being new and all is " How do i know if i have all the drivers i need? Are the drivers installed on a fresh install (ubuntu 10.04)  going to be better than anything else? Id like to say the only "card" im using is my graphics so mainly im just wondering if i have full support for my motherboard, ie. all thoese chip drivers for cpu/sound/ob wireless/network/ etc.  Im not confident in any software alone to do this yob since i come from windows..... nuf said. Should i be using a software bit to help me know what is exactly on my board then go to the appropiate driver site? I think you understand my interest. Please let me know any advice you might have. Thanks Alot People :D

---

### Post by Woody1987 on 2010-07-09
Linux comes with pretty much all the best drivers available. Exceptions are sometimes graphics and wireless. The only thing i would recommended if you havent already is to install the nvidia graphics driver in: system->administration->hardware drivers. This will give you far better 3d performance than the default one. After it is installed, in a terminal run: sudo nvidia-xconfig. Then restart. I should warn you though, there is one minor problem using this driver, the boot splash image runs at a much smaller resolution and will look ugly, but once at the desktop the screen resolution will return to normal.

---

### Post by audiomick on 2010-07-09
+1

There are proprietary drivers for graphics cards and wireless LAN cards, but your system should prompt you to install them if you need them. Otherwise, it is all there.

From what I have read, it is one of the advantages of a Linux system that the drivers are all integral to the kernel instead of being something that you have to add by hand.

---

### Post by eyeofreason on 2010-07-09
* I have an A8n32-SLI and a Crosshair both been running Ubuntu for a little over a year now. Everything you need is pretty much there except that proprietary driver for the nvidia card. If you don't get notified automatically there is always Envy. It's in the repos, it'll locate your driver for you. You may run into problems however if ever you attempt to run SLI and some issues with RAID in a striping configuration. I found help with RAID but still no support for SLI. I can't seem to get it to work.   *

---

