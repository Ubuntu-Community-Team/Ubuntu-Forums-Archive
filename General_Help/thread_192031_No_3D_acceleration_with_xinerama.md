---
title: "No 3D acceleration with xinerama?"
date: 2006-06-08
forum: General Help
---

### Post by denjin on 2006-06-08
Can someone identify what causes this problem?  I have a PCI 5700LE and then an onboard 915g to handle my 3 displays  (nvidia and i810 drivers).  How ever, I can't get anything that wants OpenGL to run.  

glxinfo says this:
```

glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

``` 
Any ideas what I'm doing wrong, or is this normal?

---

### Post by thingy on 2006-06-08
I could be wrong but after reading this, i think you can't have 3d acceleration with two different cards:

[http://lists.nluug.nl/pipermail/wurlug/2005-November/001298.html](http://lists.nluug.nl/pipermail/wurlug/2005-November/001298.html)

[http://lists.freedesktop.org/archives/xorg/2005-August/009273.html](http://lists.freedesktop.org/archives/xorg/2005-August/009273.html)

---

### Post by denjin on 2006-06-08
Thanks, thingy.  I was thinking it was something like that, but I've not been able to find any definite answer on if that is the case.  Seems rather bizarre if it is the case.  Makes me have to use Windows on this box as well for some things, which sucks even more. :(

Hmm, can you tell xinerama to only use two of the three cards? Or is it an all or nothing sort of thing?  When you have three displays, it's sometimes nice to move a window from one to the other. ;)

Edit:  I turned on twinview and just use that for two of the displays that are on the nvidia card.  But, I still don't have glx or anything with the 915g, only the nvidia one gets acceleration. No xinerama currently used.

---

### Post by denjin on 2006-06-08
Anyone have an idea?

Does installing the nvidia stuff break my openGL on the 915G side of things?

---

### Post by darkhatter on 2006-06-08
if you just use the two nvidia cards I believe you will get hardware opengl

Red Hat released a article a while back that said the drvier did break open gl for other cards (not sure if that is the same for the nvidia binary drviers that are in ubuntu) cause they applied to the drivers on nvidia.com

---

### Post by denjin on 2006-06-09
[quote=darkhatter]if you just use the two nvidia cards I believe you will get hardware opengl

Red Hat released a article a while back that said the drvier did break open gl for other cards (not sure if that is the same for the nvidia binary drviers that are in ubuntu) cause they applied to the drivers on nvidia.com[/quote]
Well, I have the hardware opengl working just fine with my nvidia card - told it to use twinview.  I suppose I can pickup a 7300GS PCIe or something and use it instead of the 915G for the 3rd monitor and then not have to worry about that opengl breakage.

---

### Post by darkhatter on 2006-06-09
I never got xinerama to work with open gl but I was using old pci video cards when I had mine so I'm not to sure about the problem

---

