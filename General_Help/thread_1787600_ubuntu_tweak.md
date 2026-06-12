---
title: "ubuntu tweak"
date: 2011-06-21
forum: General Help
---

### Post by mr.farenheit on 2011-06-21
trying to get ubuntu tweak to work in 10.04 64 bit. when using gdebi i receive this "Error: Dependency not satisfiable: python (>= 2.7). i tried looking for python 2.7 in the software center and synaptic but couldn't find it and i really don't wanna download and install it via tar.bz. anyone know how to fix this?

---

### Post by scouser73 on 2011-06-21
Hi, you can install the PPA for Ubuntu Tweak:  [[COLOR="Red"]**PPA: Ubuntu Tweak**[/COLOR]]("https://launchpad.net/~tualatrix/+archive/ppa")

---

### Post by nomko on 2011-06-21
Be advices that Ubuntu Tweak can cause serious trouble if you don't use it the correct way! You will gain access to things which bypasses the normal security system of Linux. If you don't know what you're doing Ubuntu Tweak is a mighty tool to screw youyr system. But even installing it is more then enough for screwing up your system. Myself i will never use Ubuntu Tweak. It causes all sorts of problems on my system: changing background, not able to start Nautilus with root priviliges, after changing the layout of my desktop i wasn't able to switch it back to how it was. Ubuntu Tweak screwed my system.
 
Just be warned...

---

### Post by mr.farenheit on 2011-06-21
thanks gang. i found an install in synaptic right after i posted :( i've used ubuntu tweak quite a bit but the main use was for system cleaning. thanks for the help though :lolflag:

---

### Post by nomko on 2011-06-22
Linux doesn't need to be cleaned like Windows needs. If you want to clean your system, there are 3 options:

1) install deporphan and and gtkorphan (this is for the GUI).
2) use the command sudo apt-get autoclean in a terminal
3) use the command sudo apt-get autoremove in a terminal

Deborphan cleans orphaned library files which will not be cleaned by the other 2 commands. These 3 works the best for me! I never experienced a choked up Linux system since Linux works very differently then Windows.

---

