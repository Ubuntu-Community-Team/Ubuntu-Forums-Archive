---
title: "Need help with compiz plz"
date: 2009-12-28
forum: General Help
---

### Post by Syndri on 2009-12-28
Ok i have extra effects enabled and i tried to go get compizconfig-settings-manager and it said Not available in current data. How do i get the desktop cube and flames effects?

Help would be greatly appreciated.

---

### Post by isecore on 2009-12-28
Some information would be nice. Graphics card? Have you installed the (probably) proprietary driver for it? Error messages? Dmesg output?

---

### Post by jman6495 on 2009-12-28
> **Syndri said:**
> Ok i have extra effects enabled and i tried to go get compizconfig-settings-manager and it said Not available in current data. How do i get the desktop cube and flames effects?

Help would be greatly appreciated.

try and open terminal and type
sudo apt-get install compizconfig-settings-manager
compizconfig-settings-manager

---

### Post by howefield on 2009-12-28
Try opening a terminal (Applications > Accessories > Terminal) and type

```
sudo apt-get update
```

Then try again.

---

### Post by Syndri on 2009-12-28
umm sorry i have an ATI Radeon 3100 Graphics card. It installed the drivers with no problems. It showed no errors at all.

---

### Post by Syndri on 2009-12-28
OK i tried the update thing and it worked now how do i set it up?

---

### Post by howefield on 2009-12-28
Open the settings manager (System > Preferences > CompizConfig Settings Manager.

Tick desktop cube, rotate cube, and 3D windows, if you want a sphere, check the deformation and reflection icon. Click on each icon to set the individual settings for each.

Flame text is in the Animations section (maybe extra animations) but is such a waste of time, you will soon get bored with it.

---

### Post by saadlulu on 2009-12-28
> **Syndri said:**
> OK i tried the update thing and it worked now how do i set it up?

this may help a lil, give it a shot anyway 
[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)

---

### Post by Syndri on 2009-12-28
i clicked desktop cube and hit the controls they have set as default and nothing happens :(
how do i do this lol no clue why it isnt working

---

### Post by windoze87 on 2009-12-28
This really should be in another section, but...

go to the compiz settings manager (hit alt+f2, type in ccsm, hit enter). Go to general options>desktop size. Set "horizontal desktop size" to 4. Back out of that. Make sure Desktop Cube is checked, then also check "Rotate Cube". Then click the Rotate Cube icon, set zoom to whatever you like (mine's on 1). Hold Ctrl+Alt, click your left mouse button. Bam! Magic uber cube. Move the mouse around to move the cube. You can change the horizontal desktop size to whichever you like- you can have a triangle, a pentagon, or even a dodecahedron. Enjoy. Be careful what settings you play around with in Compiz though- you can break the entire thing if you go enabling the wrong settings. Practice makes perfect. 

I do agree with one of the previous posters though... it does get old after awhile, unless you show it to a friend who only uses Windows. 

"Aero can do that?!" ...real quote. :lolflag:

---

