---
title: "Jumpy video in Ubuntu 11.04"
date: 2011-08-08
forum: General Help
---

### Post by LMartin87 on 2011-08-08
Hello there!

Im very new to Ubuntu having never used it before.

I have installed it on my netbook (Dell Mini 1010) and im having troubles playing video files such as .avi and .mkv they load up but the sounds is jumpy and the video skips/jumps so its unviewable.

Can anyone here help a newbie out please :D

Thanks in advance! :popcorn:

---

### Post by gordintoronto on 2011-08-09
Your computer is really quite slow. It just can't play HD videos smoothly.

---

### Post by LMartin87 on 2011-08-09
> **gordintoronto said:**
> Your computer is really quite slow. It just can't play HD videos smoothly.

It played them fine in Windows.

Also they are not all HD. AVI is SD that also played fine in Windows.

---

### Post by knutschr on 2011-08-09
Take a look at this site:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

> Dell Mini 10 (Inspiron 1010)
Works well. Wifi, webcam, sound playing, usb, touchpad work fine. Defaults to VESA graphics, but can be configured for accelerated 2d/3d graphics. While using the default VESA graphics, the menu (netbook-launcher) is extremely slow. Switching to accelerated graphics fixes it, or simply switch to the traditional gnome menus using Preferences... Switch Desktop Mode. See HardwareSupportComponentsVideoCardsPoulsbo for a script to fix the video on karmic.

---

### Post by LMartin87 on 2011-08-09
> **knutschr said:**
> Take a look at this site:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)


So if i 

sudo add-apt-repository ppa:gma500/emgd  sudo apt-get update sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf sudo emgd-xorg-conf[FONT=monospace]
[/FONT]It will update the drivers?

It seems that older versions of Ubuntu are more compatible than the newest. Is there anyway to get hold of the older versions?

---

### Post by Frogs Hair on 2011-08-09
If you are using Compiz and an ATI graphics card and proprietary drivers , see the third item at the link . [http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by LMartin87 on 2011-08-09
> **Frogs Hair said:**
> If you are using Compiz and an ATI graphics card and proprietary drivers , see the third item at the link . [http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

What is compiz? im completely new to this ??

---

### Post by LMartin87 on 2011-08-09
Okay got Compiz on and done what it said to do. All seems better. Going to give it a longer test see how it goes.

Thanks guys!

---

