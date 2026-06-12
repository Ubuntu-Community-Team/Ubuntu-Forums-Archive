---
title: "Cairo-dock 2 freezes"
date: 2009-10-11
forum: General Help
---

### Post by newb85 on 2009-10-11
Here's my situation.  I just did a reformat of the hd and a fresh install of Jaunty.  I ran the recommended updates through update manager and installed the interface for compizconfig and the video drivers (nvidia 180), and then I used the recommended instructions to download the recommended version of cairo-dock (according to Ubuntu community documentation - from the repository through the terminal).

Why, then, does my computer freeze every time I try to add a launcher or submenu or edit a launcher or submenu in cairo-dock?  (I can remove whatever I want; I can only add through the configuration window.)  Cairo-dock is version 2.1.0.

Another problem I experienced was that whenever the power monitor appli was enabled, starting cairo-dock in opengl would bring up a persistent configuration window.  However, because I have seen other people mention this problem (associated with different applis), I am assuming that this is an unrelated issue already being looked into by the developers.

Does anyone have ideas/suggestions?

Also, if Fabounet or another developer sees this, I would appreciate the peace of mind that the second issue is being looked at.  I would like to replace both gnome panels with cd, and since it's a laptop, being able to monitor battery level is kind of important.

THANKS!

---

### Post by newb85 on 2009-10-11
I should also mention that when I drag program shortcuts to the dock, they are not added.  When I'm holding the icon over the dock, it behaves as though it will add (existing launchers part and flashing arrows point to the gap), but once I release it, things return to normal.

---

### Post by fabounet on 2009-10-12
is it your computer that freezes or only the dock ?

about PM, what if you laucnh the dock in cairo mode ?
and if you activate the applet after you launch the dock ?
also, you can try to change the gauge, or to use a graphic instead.
thanks for your debug :-)

---

### Post by newb85 on 2009-10-12
Fabounet,
Thanks for your help.

The whole computer freezes.  Although I can still move the mouse, nothing is responsive.

The Maintenance Mode Configuration window only came up when PM was set up as a gauge and I started CD in OpenGL mode.  Activating the applet after CD was running didn't cause any issues until then next time I started CD in OpenGL.

---

### Post by fabounet on 2009-10-13
ok thanks.
I'll try to reproduce this bug.

---

### Post by nikhilbhardwaj on 2009-10-13
try without opengl
cairo-dock -c

---

### Post by newb85 on 2009-10-14
Adding a launcher freezes the machine in both cairo and opengl mode.

---

### Post by fabounet on 2009-10-15
well I don't have such freeze, maybe you can try the latest version (2.1.1-beta) available on the PPA on launchpad.net/cairo-dock
this is like the repository, but with a new version every week to get the latest fixes.

---

### Post by newb85 on 2009-10-16
Apparently, my freeze was driver-related.  When I switched my nvidia driver to version 173 instead of 180, it stopped freezing.

Thanks for your help!

---

