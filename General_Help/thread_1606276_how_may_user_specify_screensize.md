---
title: "how may user specify screensize?"
date: 2010-10-26
forum: General Help
---

### Post by gregwm on 2010-10-26
if my screen is capable of several screensizes, i can see how to list them in xorg.conf, but i don't see how to specify which one i want to use for a certain session.  ctrl-kepyad-+ will change which resolution the screen shows at the moment, but doesn't meanwhile affect the X server's idea of the screensize.  same for xrandr.  the only way i know to specify which screensize i want for a particular session is to edit xorg.conf and remove any larger screensizes.  i would expect there's a better way...?

---

### Post by gwu777 on 2010-10-26
In the latest version of ubuntu, go to system > preferences > monitors

There you can specify your screen size. xorg.conf is not really used anymore... Unless I probably do not understand your question or you are using an old ubuntu version...

---

### Post by gregwm on 2010-10-26
ok, under lxde, lxrandr changes the screensize, tho under twm, lxrandr merely changes the resolution, but the screensize doesn't change.  but with a little further google assisted research i've arrived, if i then tell twm to either f.twmrc or f.restart, it then starts using the new screensize.  thank you.

---

