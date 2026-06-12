---
title: "&quot;Input signal out of range&quot; upon startup"
date: 2009-08-10
forum: General Help
---

### Post by SoylentSteak on 2009-08-10
I get this sometimes when booting up 64 bit Jaunty. It says to set the monitor to 1280x1024 60hz, because, for some reason, upon boot it's much lower than that, until the system successfully boots. I can't use the buttons on my monitor to change this this until I get into Ubuntu, which is obviously a moot point. Once in Ubuntu, it sets itself to the right thing automatically. I've also had the same problem with earlier versions. The screen eventually goes black, and I have to reboot. On some occasions, I have to do this *literally* 50 times before I can get into Ubuntu. I did some googling, and as far as I can tell, I need to press ctrl+alt+f1, then ```
sudo dpkg-reconfigure xserver-xorg
```, and do some configuring. The only problem is, how exactly do I go about that? can I use the ```
sudo dpkg-reconfigure xserver-xorg
``` command once inside Ubuntu to keep it from having that problem in the next boot?

---

