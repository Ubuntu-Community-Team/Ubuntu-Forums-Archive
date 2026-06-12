---
title: "Virtual border around my screen?"
date: 2006-03-16
forum: General Help
---

### Post by Ivan Matveich on 2006-03-16
I've got a TV (DVI input) which: (a) has some overscan; and (b) does not respond well to tweaked video signal timings.

So, I need some way to get the window manager or X server to draw to a "virtual screen" that is smaller (by n pixels on each side) than the physical screen.

I've made a border out of gnome panels as a temporary fix, but it's far from ideal: the pointer flies off the screen in a disconcerting way, and the panels are easy to inadvertently drag around. Any ideas?

---

### Post by pak22884 on 2006-03-16
Are you running at the native resolution of the tv?  Also, is there some sort of auto adjust thing on it that you can try (or have tried)?

You might try playing with the "virtual" and "viewport" attributes under the display section in /etc/X11/xorg/conf.

I hope that's helps.

-Deepak

---

### Post by Ivan Matveich on 2006-03-17
...Xorg doesn't support virtual display sizes smaller than the physical display size.

---

### Post by pak22884 on 2006-03-18
I assume you've tried whatever auto adjust features are available on the tv.  Have you tried running at different resolutions?  I'm sorry I can't be of more help.

-Deepak

---

### Post by Ivan Matveich on 2006-03-19
Thanks anyway though; looks like I'll have to check out the Xorg source...

---

