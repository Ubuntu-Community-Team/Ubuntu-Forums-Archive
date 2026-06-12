---
title: "Graphics Going Crazy"
date: 2010-05-19
forum: General Help
---

### Post by TheHollowDeity on 2010-05-19
I recently installed Ubuntu 10.04 Netbook Remix on my Gateway LT3103u. I  noticed shortly into using it that it has a graphics bug every so  often. Especially when I change the background image. Everything will  change to a warped mix of colors and pixels. Everything is affected. My  mouse, the bar at the top of the screen, text and all. My netbook runs  on an AMD Athlon 64-bit processor with ATI Radeon X1270 HyperMemory up to 256MB  graphics. So far I have tried reinstalling, and even the 64bit desktop edition which had the same problem. Ive noticed that it freaks out when i scroll too quick, when changing background images, and on certain websites. Then other times its completely random. When it happens it looks similar to these:
[http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=155811&d=1273205203](http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=155811&d=1273205203)
[http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=155812&d=1273205203](http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=155812&d=1273205203)
Any help would be greatly appreciated!

---

### Post by dino99 on 2010-05-19
goto system admin hardware driver to see if your driver is activated.

what is your video card and which driver is installed ?
do you have compiz and/or flash installed ? (try without in case)

---

### Post by TheHollowDeity on 2010-05-19
Apparently there are no proprietary drivers in use on my netbook. :-/

also i have not installed compiz or flash yet. I've had this problem since i installed and haven't done anything except try to fix it.

My graphics card is an ATI Radeon x1270 HyperMemory

---

### Post by dino99 on 2010-05-19
delete xorg.conf, as lucid dont need it by default:

sudo rm -f /etc/X11/xorg.conf

into synaptic, check that xserver-xorg-video-radeon is installed

then reboot and recheck hardware driver

---

### Post by TheHollowDeity on 2010-05-19
Ok I followed those directions and checked the hardware drivers. The list is still empty.
:-/

---

