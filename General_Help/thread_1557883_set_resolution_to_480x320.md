---
title: "set resolution to 480x320?"
date: 2010-08-21
forum: General Help
---

### Post by markp1989 on 2010-08-21
I have installed ubuntu in a kvm virtaul machine, so i can use it via vnc from my mobile, to avoid scrolling around, i wana set the resolution of the virtual pc to be the same as the resoultion of my mobile.

in ubuntu 10.04 how do i set the resolution lower then the options on the monitor config?

thanks, mark.

---

### Post by dino99 on 2010-08-21
i think that the resolution need to be compatible with what monitor AND graphic card are able to recognise (check their specs)

---

### Post by jocko on 2010-08-21
I'm not sure how it works with a kvm virtual machine, but with virtualbox the resolution of the guest changes dynamically with the size of the window, or to the current resolution of the host display if it's running fullscreen (but the virtualbox guest additions have to be installed to get that working).
The inverse is also true, changing the resolution of the guest resizes the window, so I guess you could use xrandr to add a custom mode and set the resolution. Not  sure if xrandr works in a kvm guest, but the only way to know is by trying it...

I think running these commands in a terminal (in the guest os) should do it:
1. Find out the name of your display as xrandr sees it:
```
xrandr -q
```
It should give you an output similar to this:
```
Screen 0: minimum 64 x 64, current 640 x 480, maximum 32000 x 32000
[COLOR=Red]VBOX1[/COLOR] connected 640x480+0+0 0mm x 0mm
   688x563        60.0 +
   640x480        59.9* 
```
In my case the name of the display is [COLOR=Red]VBOX1[/COLOR], yours will be different...
2. Make a new display mode, attach it to the display and switch to it with these commands (but put your display name instead of [COLOR=Red]VBOX1[/COLOR]):
```
xrandr --newmode "480x320"   11.75  480 496 536 592  320 323 333 336 -hsync +vsync
xrandr --addmode [COLOR=Red]VBOX1[/COLOR] 480x320
xrandr --output [COLOR=Red]VBOX1[/COLOR] --mode 480x320
```


One problem you'll encounter is that the windows in most graphical applications are made for running at a minimal resolution of 640x480, so some windows will be unusable with buttons outside of the screen.

---

