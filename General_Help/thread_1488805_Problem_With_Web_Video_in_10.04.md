---
title: "Problem With Web Video in 10.04"
date: 2010-05-20
forum: General Help
---

### Post by nexoncore on 2010-05-20
I watch alot of video's online and they work fine 'ish', but when I double click for fullscreen like on youtube video's, all I get is a creamy grey screen not showing any form of video. Do you have any suggestions?

---

### Post by philinux on 2010-05-20
> **nexoncore said:**
> I watch alot of video's online and they work fine 'ish', but when I double click for fullscreen like on youtube video's, all I get is a creamy grey screen not showing any form of video. Do you have any suggestions?

System specs, video card, proprietary driver in us?
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Spr0k3t on 2010-05-20
What's your hardware setup look like (specifically video card)?  Have you tried with and without compizfusion running?  Which version of flash are you running?  Are you running 32bit or 64bit?

Answering those questions will help quite a bit.  Also, have you checked through launchpad looking through the specific flashplugin you are using?

edit: ACK!  Phil beat me to it.

---

### Post by nexoncore on 2010-05-20
Graphics is always an issue with this, I am runing embedded intel G41 chipset or a brandnew gigabyte motherboard. The intel-xorg drive seems subpar in 10.04, cant even use effects at my monitors resolution 1900 x 1020.

I have compiz completely off, no effects, no composition, nada. Just a basic gnome.

lspci gives

chris@chris-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
chris@chris-desktop:~$

---

### Post by philinux on 2010-05-20
64  bit or 32 bit install?

Flash maybe the problem.

---

### Post by nexoncore on 2010-05-20
32 bit install

---

### Post by nexoncore on 2010-05-23
I have tried all available flash programs and theres no difference, I have also opened a bug in the tracker regarding the intel-xorg driver concering other issues I am having.

Any other idea's?

---

### Post by sdowney717 on 2010-05-23
if you can switch to an nvidia card and run the nvidia driver. I can watch full screen fine.

---

### Post by nexoncore on 2010-05-23
I cant switch to nvidia, dont have an nvidia card. Found out its an issue with the intel xorg driver, need to find how to uprade it

---

