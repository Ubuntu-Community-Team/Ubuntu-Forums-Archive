---
title: "SDL mouse not working properly"
date: 2009-12-24
forum: General Help
---

### Post by sgtGarcia on 2009-12-24
Hi all.
I have a problem with games that uses SDL library & use their own mouse pointer ( Nexuiz-sdl, Postal 1&2, Quake Live, Secret Maryo Chronicles, etc.).
The problem is when I click on say a menu START (in game) then mouse pointer show in completly other place ( direction is always right+down ).
When I click somwere above+left of menu then it is possible to hit the menu.
In Quake Live when I shoot (click with mouse) my crosshair is always going down+right direction). 

Don't know why it's happening. Maybe someone else had this problem.
Can anyone help. :confused:

My comp is :
CPU:      C2Q6600
GFX:      GF9800GT with Nvidia binary driver 185 from repository install
Monitors: Samsung SyncMaster2443BW(up to 1920x1200) & AG Neovo AG-417(up to 1280x1024)
System:   Ubuntu 9.10 64bit

I've tested on both my monitors and behavior is the same.

---

### Post by sgtGarcia on 2009-12-24
bump

---

### Post by sgtGarcia on 2009-12-24
I find this problem is related to DGA.

How to test:

1.Start nexuiz with glx (nexuiz-linux-glx.sh)
2.Go to setting->input
3.Check "Turn off OS mouse acceleration" (tip -> "Make use of DGA mouse input")

than it should behave like nexuiz-linux-sdl.

I think SDL is using DGA for mouse input & this is the problem.

And it seems I found the solution.

In the xorg.conf find section "Module" & add this:

Option "omit xfree86-dga"

so it would look like this:

Section "Module"
SubSection "extmod"
Option "omit xfree86-dga"
EndSubSection
EndSection

And than every game is now working without problem.:guitar:

---

