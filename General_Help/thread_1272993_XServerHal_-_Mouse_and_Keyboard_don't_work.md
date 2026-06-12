---
title: "XServer/Hal - Mouse and Keyboard don't work"
date: 2009-09-22
forum: General Help
---

### Post by MTGap on 2009-09-22
I'm using Karmic and after I made some routine upgrades my mouse and keyboard are no longer detected. So basically everything is fine but I can't actually use the computer.

I've read that Hal is now required. I remember having troubles with Hal before where there was some error in mounting a external harddrive through dolphin. 

Hal appears to be installed and running, it however doesn't seem to be here: /etc/rc.d/hal

I tried service hal start and it said the process was running. 

I've also read that by adding:

Section ServerFlags
Option AutoAddDevices off
EndSection

to xorg.conf will fix it, but vi is making no sense to me editing in the terminal. 

How exactly can I resolve this issue easily?

---

### Post by MTGap on 2009-09-23
Bump, I would like some help.

---

### Post by MTGap on 2009-09-23
I'm bumping this again, half this forum is just stupid questions anyways.

Here's what I've tried adding to my xorg.conf based on some research I've done:

Section "ServerFlags"
	Option	"AutoAddDevices" "off"
EndSection

 
Option "AllowEmptyInput" "off"  --- To ServerLayout
Option "AllowEmptyInput" "false" --- To ServerLayout

xserver starts up but mouse and keyboard still won't work.(I put the above 3 items in separate files, I didn't put try them in the same one)

---

### Post by MTGap on 2009-09-24
......

---

### Post by MTGap on 2009-09-25
Bumpppp

---

### Post by roku151 on 2010-04-05
> Section ServerFlags
 Option AutoAddDevices off
EndSection

to xorg.conf will fix it, but vi is making no sense to me editing in the terminal. 
 
 How exactly can I resolve this issue easily?

u can use nano instead of vi
nano /etc/x11/xorg,conf

---

