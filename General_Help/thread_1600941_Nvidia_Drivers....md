---
title: "Nvidia Drivers..."
date: 2010-10-19
forum: General Help
---

### Post by Orpheon on 2010-10-19
My computer has a gforce 6200 nvidia card, which is very weak, but should still be capable of handling a few things. In Lucid things worked rather well, but maverick has some problem using that card. Not even Starcraft 1 (12 year old game) does not run without a 3-second lag on single-player, and this is just one example. I mentioned this in the beta forum and I was told that the new version of xorg is having problems. Is this still so? Another thing which I don't know whether it has something to with it is compiz. In Lucid compiz worked fine. In Maverick, the default setting in System>Preferences>Appearance>Visual effects is "None". If I try to change it, a window opens up: "Searching for available drivers...". Then it disappears, the entire screen flashes, all the windows open gray up, the bars at the top and bottom of the screen disappear, everything disappears, then the windows come back without the x - |_| buttons and all the menus. At that point I save my work and "sudo service gdm restart". The setting stays to "None". Is it the same problem? :?: System>Administration>Additional drivers tells me that nvidia-current is activated and currently in use. I am completly lost.

---

### Post by Schrute Farms on 2010-10-19
I'll give this a bump for ya.

I'd be curious to know if there are problems with this card in Maverick.  I just bought one of these cheap because my old Radeon woudn't run 10.04.  I haven't updated to .10 yet, but I'd like to know ahead of time if I can or not.

---

### Post by efflandt on 2010-10-20
Not sure which nvidia driver the 6200 uses, but they had some issues to work out for X version 1.9 that I think they resolved for the 173 drivers, but maybe not the older 96 drivers yet.

---

### Post by kumaryu on 2010-10-20
The currently recommended drivers for GeForce 6200 appear to be nvidia-173(173.1428 ) and nvidia-260(260.1912). They have both been updated to work with Xorg Xserver 1.9 in Maverick.

---

### Post by Orpheon on 2010-10-20
Thanks. What about the compiz problem? Does anybody know what this could be?

---

### Post by kumaryu on 2010-10-21
"Nvidia-current" driver is the 260.1912. 

For GeForce 6x00 and 5x00 cards, use Nvidia-173 driver (173.1428 ) instead.

Compiz will not work unless you have the appropriate drivers for your card.

---

