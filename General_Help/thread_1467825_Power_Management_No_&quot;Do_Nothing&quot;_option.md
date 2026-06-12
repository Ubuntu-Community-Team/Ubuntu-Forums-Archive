---
title: "Power Management: No &quot;Do Nothing&quot; option"
date: 2010-05-01
forum: General Help
---

### Post by windfix on 2010-05-01
I just upgraded to 10.4 and there is no longer an option to "Do Nothing" when the laptop lid is closed.  Since I use a dock and external monitors, this is a critical setting.  If I choose "Blank Screen", it blackens my externals... and I certainly don't want it to suspend or hibernate just because I dock the laptop.... 

Any fixes for this???

---

### Post by P4man on 2010-05-01
yep. Press alt+F2 and run

```
 gconf-editor
```
browse to 

/apps/gnome-power-manager/buttons/lid_ac
and
/apps/gnome-power-manager/buttons/lid_battery

set it both to  "nothing"

---

### Post by windfix on 2010-05-01
Perfect.  I had found gconf-editor by browsing other threads, but didn't locate the right fields nor values to set.  Many thanks!

---

