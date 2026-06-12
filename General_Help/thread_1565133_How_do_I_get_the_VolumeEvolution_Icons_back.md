---
title: "How do I get the Volume/Evolution Icons back?"
date: 2010-08-31
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-08-31
I removed the applet that contains them thinking i was removing the evolution icon from it.

---

### Post by arrange on 2010-08-31
I think they are two different applets anyway. The applet with the volume icon (and others) is called the *Indicator Applet* (right-click on the panel and choose *Add to panel*).

---

### Post by pqwoerituytrueiwoq on 2010-08-31
Tried that it was empty
i did find a work around 
added *gnome-volume-control-applet* to start up (prefer the other icon but this one is more useful)
Rhythmbox moved to another holder and i have empathy using it own icon
EDIT 
got the desired image on my *gnome-volume-control-applet* threw some symlinks in */usr/share/icons/ubuntu-mono-dark/status/24* 
found each panel volume icon make a symlink for them
name conversion:
*audio-volume-high-panel.svg* -> *audio-volume-high.svg*
removed the* -panel* from the file name (do with all volume icons)

---

