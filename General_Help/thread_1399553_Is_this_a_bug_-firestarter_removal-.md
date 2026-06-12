---
title: "Is this a bug??? -firestarter removal-"
date: 2010-02-05
forum: General Help
---

### Post by Barriehie on 2010-02-05
Hello All,
So I installed firestarter and then at a later date uninstalled/purged it, both actions via synaptic.  I have a very verbose boot, I like to see what's going on, and noticed after the uninstall/purge that I was getting an error zooming up the screen containing firestarter in it.  After many restarts I found that a file was left in **/etc/network/if-up.d/50firestarter** and this file was simply a script trying to restart firestarter.  At this point I've commented out the calling line and followed the commented line with exit 0.  This removes the error but there's still a link calling the file so, is this a bug or am I missing something???  It appears the uninstall/purge wasn't entirely complete.

TIA,
Barrie

---

### Post by Barriehie on 2010-02-08
I renamed the file and no issues...

---

