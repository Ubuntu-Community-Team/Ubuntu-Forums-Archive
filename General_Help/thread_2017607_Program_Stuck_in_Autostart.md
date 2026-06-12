---
title: "Program Stuck in Autostart"
date: 2012-07-05
forum: General Help
---

### Post by popppppz on 2012-07-05
Ok so new problem now, I deleted screenlets, but every time I reboot it tries to auto start anyways.  I unchecked then removed it from sessions manager auto start but it still keeps trying load then it says can't find it. Kubuntu 12.04

---

### Post by Zorael on 2012-07-08
Try looking through the following directories and make sure there aren't any screenlets scripts or .desktop files in them.
```
~/.config/autostart
~/.kde/Autostart
/usr/share/autostart
/etc/xdg/autostart
```

---

