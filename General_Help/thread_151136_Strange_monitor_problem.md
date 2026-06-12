---
title: "Strange monitor problem"
date: 2006-03-27
forum: General Help
---

### Post by mikaPELL on 2006-03-27
I have what I find a kind of strange problem. 
My laptop (a Compaq Evo N800c) has a bad screen (something with vertical lines), and at first I wanted to use my CRT monitor as a secondary monitor for reading text and such. This was possible when the laptop ran Windows, but I deleted that as soon as the computer came in my possession. Anyway, I wasn't able to figure out how to fix it so that I got different desktops on the two monitors, so I just wanted to use the CRT monitor as my primary monitor. 
I think I can recall this working the first couple of hours, but now the CRT acts as a virtual magnifying glass, and I can see only say 400 px around the cursor at all times. When I run smaller resolutions, I can see a higher percentage of the desktop, but it is really useless at e.g. 1600x1200 as I normally run.
Any suggestions on how to either get dual monitors working, or even just the same desktop on both monitors are greatly appreciated.

PS: I use an ATI Radeon 9000 Mobility.

--Mikael

---

### Post by mikaPELL on 2006-03-31
[[IMG]http://img86.imageshack.us/img86/465/dsc008513ko.th.jpg[/IMG]](http://img86.imageshack.us/my.php?image=dsc008513ko.jpg)
Here's a photo I took earlier, just to show the problem clearer. Still not any suggestions? :(

---

### Post by Perfect Storm on 2006-03-31
Have you tried with
```
sudo dpkg-reconfigure xserver-xorg
```

That might help. I've seen a howto on Dualmonitors but it's for Nvidia cards. [http://doc.gwos.org/index.php/DualMonitors](http://doc.gwos.org/index.php/DualMonitors)

---

### Post by mikaPELL on 2006-04-01
[QUOTE=Artificial Intelligence]Have you tried with
```
sudo dpkg-reconfigure xserver-xorg
```

That might help. I've seen a howto on Dualmonitors but it's for Nvidia cards. [http://doc.gwos.org/index.php/DualMonitors](http://doc.gwos.org/index.php/DualMonitors)[/QUOTE]
Yes, several times. I've also tried stopping gdm before doing so, but it looks all the same as when no external monitor is connected. Thanks anyway

---

