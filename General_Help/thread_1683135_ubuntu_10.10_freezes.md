---
title: "ubuntu 10.10 freezes"
date: 2011-02-07
forum: General Help
---

### Post by ubun2warrior on 2011-02-07
hi 

i have an acer laptop, dualcore pro, 2 gb ram, 320 gb harddisk.

i dual boot ubuntu 10.10 with vista.i install ubuntu inside windows.(for any further info plz specify)

from time to time the screen freezes and nothing moves, mouse cursor does not move at all and sometimes keyboard works.
this happens all of a sudden, i am doing something and then suddenly it freezes not the grey freezing that occurs sometimes when a window is misbehaving but a normal freeze like its jammed, stopped working.

kindly explain why this trouble.

i even reinstalled ubuntu several times but the same problem is there.

i have even tried ubuntu 10.04 lts, this problem is not there. but there is another problem with 10.04. the screen flickers from time to time. i.e white lines start coming in between as if there is some problems with the display screen. 

But with vista i have faced no such trouble, is there some bug of some type

plz help me out, i thoroughly enjoy working in ubuntu but this trouble is very annoying. i have been facing this since the very beginning i.e from the time both these os's were released. from April with 10.04 and october with 10.10.

regards

---

### Post by P4man on 2011-02-07
Sounds like it could be an issue with graphics card/driver. Do you know what graphics card you have in that machine? IF not, can you open a terminal (applications > accessories > terminal) and type in the following command:

```
lspci
```
copy/paste the output here.

Ad interim, you can already disable desktop effects in system > administration > appearance > visual effects. Set them to none. See if that helps.

---

### Post by leviathan8 on 2011-02-07
This is a common issue on laptops, as far as I experienced it.
It did happen to me too, and what it did to solve it, was the following: *first make sure you have bum (boot-up manager) installed, fire it up and disable start-up processes like: saned, cups, bluetooth, and anything else you consider that could contribute to the freeze. Next off, disable any hardware driver, but do keep the wireless internet driver - guess you will always need it. Most of the time, this could be a graphics card problem, so go on and put effects to *None* in appearance menu, and also, from System -> Administration -> Login screen, set GDM to automatically drop you to the desktop (in other words, disable the login screen). If you have installed any programs like acpi, powertop and laptop-power-utils (not sure if this is the name), purge them! 
Oh, did I mention to unplug any input devices (mice, usb sticks, etc) and see if it works fine w/o them?

Later edit: I wasn't on my laptop at the time I wrote the post, so here are some completions;
Under the power management preferences, set them as in the picture:

[IMG]http://i.imgur.com/rqtia.png[/IMG]

[IMG]http://i.imgur.com/SXhPt.png[/IMG]

Try everything, I hope it will help you, greets!

---

