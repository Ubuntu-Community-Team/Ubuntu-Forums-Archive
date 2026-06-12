---
title: "over-large fonts in KDE apps"
date: 2004-10-21
forum: General Help
---

### Post by jeremy on 2004-10-21
I use, and like, gnome, but there are a couple of KDE apps I cannot do without; Quanta (kdewebdev 3.3.1) and k3b, in bith these programmes the fonts are very big (using gnome apps, all is fine), is there any way to change this?

edit/add
My screen res. is 1600 x 1200, it is as if the kde apps think it is, say, 1024 x 768.

---

### Post by bantu on 2004-10-21
An easy way out is to install kcontrol. In the control center - section look and feel - you can change the font size.

Regards, bantu

---

### Post by jeremy on 2004-10-21
Excellent! Many thanks.

---

### Post by williamroddy on 2004-10-21
Also, another thing to factor in is the fact that Ubuntu uses GDM instead of KDM influences font size. So does the font sizes used by root, if you are a user accessing root-controlled programs. So, a few compromises and adjustments must be made from one display manager to the other, since KDE usually uses "kdm."

You can change this setting in /etc/X11/default-display-manager

This also changes the log-on screen.

My humble opinion after having been a long-time KDE users is that, overall GDM is nicer. But that's only my opinion and only as of this moment.

Toward peace,
Wil

---

