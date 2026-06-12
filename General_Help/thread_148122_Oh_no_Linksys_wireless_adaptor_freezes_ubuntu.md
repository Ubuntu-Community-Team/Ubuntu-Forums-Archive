---
title: "Oh no Linksys wireless adaptor freezes ubuntu"
date: 2006-03-21
forum: General Help
---

### Post by ade234uk on 2006-03-21
I just bought a new wireless adaptor because it is meant to work straight out Its a linksys Wireless G adaptor WMP54G

When I goto to network I can see it already there :D but then when I got to click enable this device Ubuntu totally freezes up on me :( 

I have tried a differenct pci slot, I have also totally reinstalled Ubuntu without any luck whatsoever.

Is there any way of starting / enabling this device through the terminal? Has anyone else experienced this?

---

### Post by Ramses de Norre on 2006-03-21
I've encountered such freezes allready on devices with wrongly compiled drivers.
So maybe the driver is corrupted.. Though I don't really now what to do then..

---

### Post by LuisC-SM on 2006-03-21
[QUOTE=ade234uk]I just bought a new wireless adaptor because it is meant to work straight out Its a linksys Wireless G adaptor WMP54G

When I goto to network I can see it already there :D but then when I got to click enable this device Ubuntu totally freezes up on me :( 

I have tried a differenct pci slot, I have also totally reinstalled Ubuntu without any luck whatsoever.

Is there any way of starting / enabling this device through the terminal? Has anyone else experienced this?[/QUOTE]

You probabily used the driver that came on the CD.

If so... then forget it, use the driver provided in [www.realtek.com.tw](www.realtek.com.tw) and look for RTL8180L. DL the one that says Windows XP and install it with ndiswrapper.

There are several tutorials to install it (HOW-TOs) on the wikis.

Hope it helps.

Luis C. Suárez

---

