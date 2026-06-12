---
title: "Lost Volume Control"
date: 2011-07-15
forum: General Help
---

### Post by mcman56 on 2011-07-15
When I first loaded Ubuntu, there was some sort of volume control always available on the desk top. It has since disappeared. I can go to System and get a volume control but it disappears on reboot. Is there a way to get the original one back?

---

### Post by Frogs Hair on 2011-07-15
Try the command to restore panel to defaults.```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

---

### Post by mcman56 on 2011-07-16
That worked.  Thanks!

---

### Post by Frogs Hair on 2011-07-16
You're Welcome .

---

