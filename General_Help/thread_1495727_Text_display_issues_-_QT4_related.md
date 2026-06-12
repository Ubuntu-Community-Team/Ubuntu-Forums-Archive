---
title: "Text display issues - QT4 related?"
date: 2010-05-28
forum: General Help
---

### Post by silospen on 2010-05-28
Hello,

I've searched everywhere and I can't find an issue similar to the one I have. 

Basic process is that I switch from a window to another one and when I switch back, the text is blurry, totally unreadable (see picture). I then have to minimize and then restore that window and it goes back to normal, usually when an action is performed that goes over the blurred text. It happens about 4 - 5 times an hour.

I only see it in specific applications:

* Kile
* QT Assistant
* KTorrent
* A QT4 C++ app that I'm developing (see picture)

Everything else works fine, no blurring of fonts.

These are all KDE/QT4 applications, so I'm assuming that has some relation. Perhaps since I'm running Gnome, I'm missing some font/graphics setting?

I'm running Linux Mint 7 Gloria - Main Edition (Ubuntu 9.04/Jaunty) on a HP pavillion dv6000 laptop with an NVidia GeForce Go 7400 (I think) and driver nvidia_drv.so.

Any ideas?

---

### Post by dino99 on 2010-05-28
check the languages packages installed and the language settings with these apps

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by silospen on 2010-05-28
> **dino99 said:**
> check the languages packages installed and the language settings with these apps

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

Yup, they're all installed.

---

