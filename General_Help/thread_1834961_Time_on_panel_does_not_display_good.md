---
title: "Time on panel does not display good"
date: 2011-08-28
forum: General Help
---

### Post by Marco.75 on 2011-08-28
Hi, I need help for a little annoiance in Ubuntu 11.04.
I'm running Ubuntu 11.04 (classic gnome desktop) and on the upper right corner, just before the shut-down icon, the time isn't displayed properly. It should say "Sun 28 Aug 18:32" and instead the last digit is somehow truncated and I read "Sun 28 Aug 18:3".
If I set the applet properties to show seconds, even the last digit of them appears truncated, but oddingly when I deselect the seconds, minutes show right untill next login.
Also, I have the impression that the whole applet is using slightly bigger characters than the ones used in the main menu and in the applications.

---

### Post by dino99 on 2011-08-28
try either: move it to an other place (by right-click) or remove then reinstall it.
at least into a terminal, either:
gnome-panel --replace
unity --reset
(depending of what is used)

---

### Post by Marco.75 on 2011-08-28
moving it doesn't work, because it moves the time string along with the network applet the shotdown button etc... they are a whole.
Neither gnome-panel --replace works

If I lower the DPI or the fonts dimensions for the gnome apps, time displays correctly but fonts on menu and apps become way too little.

---

