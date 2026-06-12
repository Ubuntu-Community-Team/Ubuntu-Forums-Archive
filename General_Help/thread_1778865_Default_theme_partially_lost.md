---
title: "Default theme partially lost"
date: 2011-06-09
forum: General Help
---

### Post by Gen2ly on 2011-06-09
I started up today and everything is running fine but ubuntu's default theme now is only partially showing.  Icons and the panel bars now show Gnome's default look.  Tried to select a different theme in the Appearance CP and going back to Ambiance but had no luck.  Any ideas on what I an do?  Attached screenshot.

---

### Post by MSPdwalt on 2011-06-09
Hit alt-F2 and run the following:

```
gnome-settings-daemon
``` - re-applies your gnome theme
```
killall nautilus
``` - restarts nautilus so the correct theme applies

kill and restart any other open apps.

There's a few other threads on this. It's a known bug, not sure it's fixed yet.  I still see it occasionally on my laptop.

---

