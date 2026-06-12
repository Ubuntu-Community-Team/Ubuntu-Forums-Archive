---
title: "When typing, mouse stops moving"
date: 2012-06-10
forum: General Help
---

### Post by Gikoskos on 2012-06-10
Hi all,
i did a clean installation of Ubuntu 12.04 recently and all is well, except
for one small thing. When i type anything and anywhere with the keyboard, i cant move the mouse. So for example when i am playing a game which requires two hands like Nexuiz, i can only move the character but i cannot turn around simultaneously.
Ubuntu runs on a desktop PC. I have a standard cheap Logitech keyboard and the 
most common Microsoft mouse. I tried connecting the keyboard or the mouse, or both together on the PS/2 hub but it's still the same.
Any suggestions considering the solution of this problem are welcome:P.
Thanks in advance to anyone who replies.

---

### Post by Fuzzv on 2012-06-10
There is a setting called "disable touchpad while typing" that is meant for laptops, but it sounds like it may be causing your difficulty here. [See if you can disable "disable-while-typing" with this method.]("http://www.upubuntu.com/2011/11/is-your-laptop-touchpad-not-working.html")

---

### Post by Gikoskos on 2012-06-10
Hi and thanks for the reply.
Yes i forgot to mention that i already tried the 'Disable when Typing' from the 
d-conftools but still nothing happens:(

---

### Post by Gikoskos on 2012-06-10
Please if anyone knows any possible solution to this problem, just say it.
I opened a same thread two weeks ago but there were no replies.:confused:

---

### Post by Ubun2to on 2012-06-10
Have you ever tried the Xbox Live Controller for PC? There are built in drivers in Ubuntu, and I am in love with it!

---

### Post by Gikoskos on 2012-06-10
> **Ubun2to said:**
> Have you ever tried the Xbox Live Controller for PC? There are built in drivers in Ubuntu, and I am in love with it!
Yeah, i have no problems with the controllers and the joysticks.
All of them work wonderfully. But this problem isn't only on games.
I have it everywhere on the Ubuntu desktop. All applications such as Libreoffice, Nautilus
etc. have this problem; when i type with the keyboard the mouse stucks in one position and i cannot move it until i stop typing.

---

### Post by Ubun2to on 2012-06-11
> **Gikoskos said:**
> Yeah, i have no problems with the controllers and the joysticks.
All of them work wonderfully. But this problem isn't only on games.
I have it everywhere on the Ubuntu desktop. All applications such as Libreoffice, Nautilus
etc. have this problem; when i type with the keyboard the mouse stucks in one position and i cannot move it until i stop typing.

Oh. Well, I have never encountered this problem. I think you mentioned something about using PS/2 devices. Maybe that's the problem. Maybe you need a new keyboard and mouse, ones that use USB (which can be as cheap as $3 on Amazon.com, where I bought my new keyboard and mouse).

---

### Post by Howard Hatecraft on 2012-07-01
i opened a thread some days ago concerning the same problem. my usb mouse is stuck for ~half a second whenever i type on my laptop keyboard. i tried a different mouse and different usb plugs - the problem remained. enabling the touchpad while typing didn't help, anyway, this option doesn't give any response. when i type, my touchpad is always working, my mouse never. :evil:

edit: recently i tried to install nvidia drivers, but i decided to remove them again and use bumblebee with intel drivers (as i found websides suggesting editing xorg.conf)

---

### Post by goltoof on 2012-07-01
Im also having issues with mouse and keyboard working together in harmony.  Except my mouse stops grabbing or right clicking and hotkeys do nothing.

Theres just got to be somethngi to redo in the system to make sure mouse/keyboard continues working without interruption but i have yet to find it..

---

### Post by Howard Hatecraft on 2012-07-05
some news: i solved the problem with "echo n > /sys/module/usbcore/parameters/autosuspend" and replugging the mouse but it's not permanent and honestly i'm not sure what i'm doing. 

i'm running tlp with autosuspend off. output of tlp-usblist:

Bus 001 Device 010 ID xxxx:xxxx control = on,   autosuspend_delay_ms =  2000 -- Logitech, Inc. MX510 Optical Mouse (usbhid)

every other device is on "auto" instead of "on". by running tlp-usblist, the problem appears again. any idea?

---

