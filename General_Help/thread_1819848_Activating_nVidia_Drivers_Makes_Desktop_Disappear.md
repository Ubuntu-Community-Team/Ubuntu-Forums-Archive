---
title: "Activating nVidia Drivers Makes Desktop Disappear"
date: 2011-08-06
forum: General Help
---

### Post by Jack14112 on 2011-08-06
When I activate the nvidia and restart, the desktop disappears. I have tried re-installing Ubuntu and mint and it keep happening. The computer is has a single core amd athlon 64, 1.5gb's of ram and a nvidia 7300gs card.

---

### Post by wildmanne39 on 2011-08-06
Hi, please explain.
Do you get the unity desktop? Move your all the way to the left of the screen does the launcher come out?

Does your system boot at all?
Thank you

---

### Post by Jack14112 on 2011-08-06
Yeah It boots and I can login but when it logs in the desktop wont load I can just see the background. Well the first time I installed Ubuntu I could see the desktop but I couldn't click on anything, just move the mouse.

---

### Post by sinbowden on 2011-08-06
> **Jack14112 said:**
> When I activate the nvidia and restart, the desktop disappears. I have tried re-installing Ubuntu and mint and it keep happening. The computer is has a single core amd athlon 64, 1.5gb's of ram and a nvidia 7300gs card.


Hello, follow step 4 and see if that works...
[http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html](http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html)

---

### Post by Jack14112 on 2011-08-06
> **sinbowden said:**
> Hello, follow step 4 and see if that works...
[http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html](http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html)


Yeah, that's what I'm doing apart for Ubuntu prompts me to install it and I just select the recommended one.

---

### Post by wildmanne39 on 2011-08-06
Hi, what version of ubuntu are you using?

---

### Post by Jack14112 on 2011-08-06
> **wildmanne39 said:**
> hi, what version of ubuntu are you using?

11.4

---

### Post by wildmanne39 on 2011-08-06
Hi, at the log in screen click on your user name then go to the bottom of the screen and choose ubuntu with no effects and see if that will load.

---

### Post by Jack14112 on 2011-08-06
> **wildmanne39 said:**
> Hi, at the log in screen click on your user name then go to the bottom of the screen and choose ubuntu with no effects and see if that will load.

I tried that, still nothing.

---

### Post by wildmanne39 on 2011-08-06
Hi, try this hold down the shift key when you boot your system, then in the grub menu choose recovery, in the next screen choose root with network.
Then run these two commands:
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```
Then restart your computer.
Thank you

---

