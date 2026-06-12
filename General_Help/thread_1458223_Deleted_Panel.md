---
title: "Deleted Panel"
date: 2010-04-19
forum: General Help
---

### Post by Cubhicbu on 2010-04-19
I deleted my taskbar panel. How can I get it back?

I prefer to use a dock, and so I'm using Cairo-dock, and because of this, I deleted my taskbar panel, and I was just wondering how I would get it back, if I ever wanted to.

---

### Post by howefield on 2010-04-19
Do you still have the top panel ?

Right click it and select New Panel, then right click that new panel and select Add to Panel to add back the applets as required.

---

### Post by sisco311 on 2010-04-19
You can run:
```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```
to restore the default panels.

---

