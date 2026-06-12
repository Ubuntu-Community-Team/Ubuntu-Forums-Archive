---
title: "LyX is slooooww..."
date: 2011-03-29
forum: General Help
---

### Post by sleepingdragon on 2011-03-29
I don't know whether this is just me or not, but I'm finding LyX to be incredibly slow, down to the point that it's chasing the words that I'm typing. There seems to be no errors given and all the commands behave as expected - eventually. Other (LA)TEX editors seem to behave just fine.

I know it's not a CPU issue, I'm on a Core2Duo @ 2.4Ghz and 2GB RAM, every other application runs smoothly.

Anyone else had the same problem?

---

### Post by baytuni on 2011-04-09
right here

---

### Post by sleepingdragon on 2011-06-22
Right. Time for something weird. LyX is working at normal speed in KDE, but not in Gnome. Both tested on 11.04.

Any ideas?

---

### Post by 334455 on 2011-06-23
Check out this page: [http://wiki.lyx.org/Tips/PerformanceIssues](http://wiki.lyx.org/Tips/PerformanceIssues). Especially the advice to add subsection to /etc/X11/xorg.conf could be worth testing.

---

### Post by MisterLambda on 2011-06-23
I'm pretty sure LyX is a Qt app. KDE is Qt based, so LyX has most of the libraries needed already loaded, whereas it has to load most of them from scratch from GNOME, which doesn't use Qt.

---

