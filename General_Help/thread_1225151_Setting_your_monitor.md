---
title: "Setting your monitor"
date: 2009-07-28
forum: General Help
---

### Post by undeadboe on 2009-07-28
How do I set my monitor to 60hz? My monitor is causing me problems on startup

---

### Post by kerry_s on 2009-07-28
first find what it runs at, i used the info button on my monitor.
then edit the xorg.conf:
[B]press alt+f2
gksudo mousepad /etc/X11/xorg.conf[/B]

example:
```
Section "Monitor"
    HorizSync     30-60
    VertRefresh   55-61
EndSection
```

(the example is just a guess, mines running at 70)

---

