---
title: "X server faliure"
date: 2006-05-14
forum: General Help
---

### Post by adamgfry on 2006-05-14
I installed ubuntu about 1 hour ago, and was horrified to get the message Xserver falied, restarting. It then came up with no graphical interface. I think X server has probaly got something to do with my graphics card. Can someone tell me what is wrong???

My graphics card is a ATI Radeon Express 200, with an acer TFT moniter.

---

### Post by Ramses de Norre on 2006-05-14
You can try this: (worked for my ati)
You probably get dropped to a shell, if not press ctrl+alt+F1 to get to one.
Then enter following commands:
```
sudo cp -p /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo vi /etc/X11/xorg.conf
```
Search the device section for your video card, press i to go into insert mode and change the driver (probably ati or radeon now) to vesa. Then press esc, shift+q, type wq! and enter.
Then type ```
sudo /etc/init.d/gdm restart
```
It will give you the graphical login, if your problem is the same as I've got.
Search the forums on how to install the fglrx driver then because you don't want to keep using vesa (no accel).

---

