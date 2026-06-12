---
title: "well, the (un)usual graphics card problems"
date: 2009-11-26
forum: General Help
---

### Post by mrhippieguy on 2009-11-26
first of all, i have a VisionTek Radeon X1300 XGE 512MB. and second, the console is still a bit of a novelty to me(as in i can only do most the basic things).

so i know that 9.3 driver installer doesn't work with 9.04/.10, so i'm still using 8.04.. now my trouble is that, well, i'm a 3d graphic designer. i need my video card to be working, and i work on a budget of $0.00(got my computer, ram, graphics card, monitor, and 3d development software for free).

what happens is i start it up, then it works fer a few times. then, suddenly, i start it up, and right after the loading screen, i see some console lines that say something about 'starting anac(h)ronistic cron anacron' or somthing. then, funky random green 'n' black colorbars, then dialog box.('Ubuntu is running in low-graphics mode') and i can't use glsl, can't even set my screen res higher than 800x600. the only fix that works is reinstalling ubuntu, but that ony works for a short time, and after twenty times this week, it's getting stupid.

help is appreciated, and very much needed.

---

### Post by mrhippieguy on 2009-11-26
no ideas? sorry i'm so pushy, i had a double espresso with extra sugar and cinnamon so right now, it feels like three weeks ago isn't soon enough.

---

### Post by jacobs444 on 2009-11-26
try this in terminal 
sudo dpkg-reconfigure xserver-xorg

---

### Post by mrhippieguy on 2009-11-26
thank you dude, but, just slightly too late. i just reinstalled ubuntu(freakin coffee. makin me so damn impatient). not to worry, though, i work mostly off of a flash drive. if it happens again(which i'm pretty sure it will), i'll try that.

---

