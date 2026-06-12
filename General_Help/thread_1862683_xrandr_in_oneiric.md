---
title: "xrandr in oneiric"
date: 2011-10-17
forum: General Help
---

### Post by wildtron on 2011-10-17
after upgrading from natty to oneiric.. everything was working fine until i checked my way of changing the screen resolution of my net book... it was working in natty but after the upgrade to oneiric it worked but there something wrong.. after i changed the resolution i noticed that there is like an invisible wall bounding my mouse... but the windows are not bounded... can anyone help??

i use this command in terminal to change my resolution:

xrandr --mode 1024x600 --output LVDS1 --scale 1.30x1.30 --panning 1331x778

---

### Post by oldmansutton on 2011-10-17
I have the exact same problem.  I resize my netbook desktop by stretching it beyond the allowed screen resolution with Xrandr, but my mouse stays within the bounds of the maximum resolution, not within the bounds of the new "stretched" resolution.

---

### Post by Master One on 2011-10-18
This may have something to do with my experienced problem, which I have described [here](http://ubuntuforums.org/showthread.php?t=1863758).

Somehow the "Desktop" does not get updated on resolution changes, so stays stuck in the initial resolution, causing a smaller or larger Desktop/Workspace then the actual screen-resolution.

I have not found a solution to my problem with my video projector yet.

---

### Post by qkzoo on 2011-10-18
I, too, would like a solution to this problem.  It is quite debilitating!

Q

---

