---
title: "Asus R1 Tablet"
date: 2011-05-15
forum: General Help
---

### Post by djmickyg on 2011-05-15
Hi, 
I've just installed ubuntu 11.4 on my Asus R1, so far almost everything works. it starts up in 1/4 of the time windows did, the digitiser pen works great.
The only thing I can't get working is the screen rotation when the screen is flipped.
I have found a few scripts that work with 10.4 but they don't seem to work with 11.4
If I manually rotate the screen in the settings, the mouse and digitiser pen don't rotate so they are 90deg out.. 

anyone have a solution?

---

### Post by Favux on 2011-05-15
Hi djmickyg,

Right now there is a bug in the default xf86-input-wacom-0.10.11 where cw and ccw are swapped.  A patch to fix it was accepted Thursday but hasn't yet been committed to the xf86-input-wacom git repository.  That will probably happen Sunday evening/Monday.  Then you can clone the git repository for version 0.11.0+ as described in the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") Part II c).  Then rotation will work correctly.  In the meantime in the scripts just swap the xsetwacom cw and ccw commands.

---

### Post by djmickyg on 2011-05-15
thanks for the quick reply, 
I will give this a shot when I get home. 
Is this an update that will be pushed out with the normal ubuntu updates?

also, does this fix auto rotate the screen when the screen is flipped/rotate button is pressed? or does it only fix the rotation when the settings/display rotation is changed?

---

