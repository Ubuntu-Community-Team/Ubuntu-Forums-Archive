---
title: "1/2 of the screen is blank after starting a 3D game..."
date: 2010-08-31
forum: General Help
---

### Post by brclancy111 on 2010-08-31
Hi! I'm using a toshiba laptop {w/ Ubuntu Desktop 64-bit edition}

Whenever I open the [hard-core] resolution-editing full-screen games, I either get a blank screen that covers the top half of the screen, or a X-Freeze...

Previously, I've been able to run starcraft 2, and other large games via windows.. but this can't even play simpler games, such as tremulous without these weird problems occuring...

on the 1/2 screen freeze, I can see my mouse over it, but I can't drag anything past it... Almost it's like the top panel, but extended all of the way down...

It seems like I can actually click the taskbar behind it...

ignore the black (it did that for some reason...) look at the purple :P
[IMG]http://i498.photobucket.com/albums/rr350/brclancy111/Screenshot-1.png?t=1283230553[/IMG]

---

### Post by varunendra on 2010-09-01
Please post model no. of your laptop and the model of graphic card it is using if you know it.

Additionally, post the output of the following:
Before or after the resolution change:-
```
sudo lshw -C display
```

Only after the resolution change:-
```
dmesg | tail
```

From the screenshot it appears that your game is trying to set the screen ratio to 16:9 (widescreen) while your screen's physical dimensions are 4:3. If you can permanently set your game's graphic properties to use a resolution of aspect ratio 4:3 (like 800x600, 1024x768,..... etc.) then maybe it'll get fixed itself. Otherwise I guess you need a better driver for your graphics.

---

