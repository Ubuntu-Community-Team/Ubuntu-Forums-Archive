---
title: "[ubuntu 10.04]Icons with white background in Gnome-Panel"
date: 2010-05-03
forum: General Help
---

### Post by mirkos90 on 2010-05-03
Hi, I have a problem  with Ubuntu 4.10 and gnome-panel ... The new icons  are very nice, but if I go to open software like vlc or banshee get  similar results:[IMG]http://www.google.it/images/cleardot.gif[/IMG]

[IMG]http://i43.tinypic.com/xp7nzb.png[/IMG]

(See at the end of panel the icons of VLC and banshee)

I think  a screenshot is worth a thousand words, how to resolve?

Thank  you all in advance!
Mirko

---

### Post by mirkos90 on 2010-05-03
bump :(

Mirko

---

### Post by mirkos90 on 2010-05-04
...bump^2 :|

Mirko

---

### Post by dino99 on 2010-05-04
metacity --replace

sudo dpkg --configure -a

---

### Post by mirkos90 on 2010-05-04
> **dino99 said:**
> metacity --replace

sudo dpkg --configure -a
Hi, thanks for answer... but nothing... I do ur commands and I open VLC, but the result is  equal...

Thanks again..
Mirko

---

### Post by mirkos90 on 2010-05-05
Uhm.. bump...
Please help me :(

Mirko

---

### Post by munky99999 on 2010-05-08
[http://ubuntuforums.org/showthread.php?t=1427968&highlight=notification+tray](http://ubuntuforums.org/showthread.php?t=1427968&highlight=notification+tray)

appears to happen for all transparent ones.

ubuntu wants to remove the tray entirely. Which is insane.

---

### Post by mirkos90 on 2010-05-09
> **munky99999 said:**
> [http://ubuntuforums.org/showthread.php?t=1427968&highlight=notification+tray](http://ubuntuforums.org/showthread.php?t=1427968&highlight=notification+tray)

appears to happen for all transparent ones.

ubuntu wants to remove the tray entirely. Which is insane.
o,o uau :|
And so... there aren't solutions for this problem? :S

Mirko

---

### Post by stickerpoint on 2010-05-09
using 10.04:

If you want to use Cairo-dock, or something similar like I do, then I found the following method the easiest way (I have not found a way of removing the last panel completely either).

You don't need to remove all the icons etc. - just create a new panel on top of the other, and then remove it. You should be left with an empty panel. Reduce this as much as possible by right-clicking on the properties, auto-hiding etc., and put it under the Cairo-dock, which in my case is set to stay visible at the bottom of the screen.

After a reboot, I must say that I cannot see the panel, nor even auto-hide the Cairo-dock and get to the panel!

Anyway, hope that helps - not a complete solution for those looking for the perfect world, but it works.

---

### Post by jamessimo on 2011-01-05
> **munky99999 said:**
> [http://ubuntuforums.org/showthread.php?t=1427968&highlight=notification+tray](http://ubuntuforums.org/showthread.php?t=1427968&highlight=notification+tray)

appears to happen for all transparent ones.

ubuntu wants to remove the tray entirely. Which is insane.

Follow this link to like page 4 or 5, it fixes it!

---

