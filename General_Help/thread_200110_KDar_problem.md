---
title: "KDar problem"
date: 2006-06-19
forum: General Help
---

### Post by Fred Doolie on 2006-06-19
When I do a full backup with KDar I get LOTS of permission errors (of course). It looks like KDar need to be run as root...but the login screen refuses to let "root" log in. "Can't log in that way" or something.  Is there a way to make a launcher for KDar that automatically runs it through sudo or something?

---

### Post by aysiu on 2006-06-19
```
kdesu kdar
``` for KDE or ```
gksudo kdar
``` for Gnome.

---

