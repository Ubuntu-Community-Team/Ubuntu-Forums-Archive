---
title: "Deleted off panel...???"
date: 2011-01-27
forum: General Help
---

### Post by robertcoulson on 2011-01-27
Can some one help...Deleted mute / unmute speaker (sound) icon from panel...??
Robert

---

### Post by nothingspecial on 2011-01-27
Right click the panel and add it back

---

### Post by OxentroT on 2011-01-27
Right-Click on your panel and then click on +Add To Panel and search for 'Notification Area' and add that to your panel.

---

### Post by robertcoulson on 2011-01-27
OxentroT...Tried that...I can see it,but it will not add when I click the add button...I just added "sound preferences" for now...Does the same thing, but wish I had the other icon...Thanks anyway.
Robert

---

### Post by thewho1050 on 2011-01-27
Try right click add indicator applet.  The speaker identifies itself as an indicator applet.

GL

---

### Post by robertcoulson on 2011-01-27
thewho1050...Got my "mail" and my "speaker" back...Thank you..Now one more stupid thing I did..Was trying to remove a "separator" line and I LOST my "Wifi" indicator....Yikes
Robert

---

### Post by robertcoulson on 2011-01-27
Never mind ...got it back...Thanks guys (or girls).
Robert

---

### Post by lordjj on 2011-02-14
I know the issue's solved, but just for the future, whenever you screw up anything with the panels you can reset them:
```

gconftool-2 --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```
(You can even do this while you have no visible panels at all -and no apparent access to Terminal; just press alt+f2 and enter the 3 commands one by one)

---

