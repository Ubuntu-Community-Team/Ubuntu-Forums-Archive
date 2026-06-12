---
title: "OpenGL issues with fglrx"
date: 2011-08-13
forum: General Help
---

### Post by thewaffler100 on 2011-08-13
Hello, I have recently installed Xubuntu 11.04 on my laptop. The default radeon driver is too slow, so I decided to install the fglrx driver. Installed it, and 3D acceleration improved. But here comes the weird bit, I went to the screensaver settings, and none of the screensavers, except for FuzzyFlakes and FiberLamp worked. All the other screensavers don't load and it says it terminated with signal 11. 3D Acceleration really brought up the frame rates for those only two working screensavers. I can't play any game that uses OpenGL. Super Tux for example, would crash if I check the "OpenGL" option. I appreciate anybody's help. Thank you. 

By the way, my chipset is a ATI Radeon x1200..

---

### Post by Mark Phelps on 2011-08-14
You should have checked here first -- BEFORE forcing a driver onto your PC that will not work with your card.

ATI dropped fglrx support for that card years ago, and the only drivers that would work -- are the ones you removed.

You should read through the post below regarding how to remove the fglrx drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Also, while this will restore desktop graphics, it will not provide hardware acceleration.  To get that, you would have to upgrade to one of the new "HD" 3x/4x/5x/6x cards that IS supported.

---

### Post by thewaffler100 on 2011-08-14
Really? Aw, that sucks. Well thank you for responding.

---

