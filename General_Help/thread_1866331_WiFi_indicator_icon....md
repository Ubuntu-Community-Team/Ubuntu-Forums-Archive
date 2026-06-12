---
title: "WiFi indicator icon...???"
date: 2011-10-21
forum: General Help
---

### Post by robertcoulson on 2011-10-21
Hi
Can anyone help...I lost my WiFi bar indicator icon that was on my panel bar at the top of my screen...I don't know how to get it back there....???

Robert

---

### Post by duke.tim on 2011-10-26
Try this 
```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

---

