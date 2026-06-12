---
title: "Deleted top panel"
date: 2010-01-04
forum: General Help
---

### Post by Final Version on 2010-01-04
I deleted the top panel, how can I restore it to default.

---

### Post by MelDJ on 2010-01-04
try this: [http://ubuntuforums.org/showthread.php?t=189408](http://ubuntuforums.org/showthread.php?t=189408) to launch a terminal. then type gnome-panel to run the panel and then go back to your desktop

---

### Post by Final Version on 2010-01-04
Just says "A panel is already running."

---

### Post by Groundswell on 2010-01-04
do you still have a bottom panel?

---

### Post by Saiko Berry on 2010-01-04
If you removed both, you can;

gconftool-2 --recursive-unset /apps/panel
gnome-panel

But if you only removed one, add it back by right clicking the bottom and hitting add panel.

---

### Post by warfacegod on 2010-01-04
Right click your other panel, select new panel.

---

### Post by Final Version on 2010-01-04
> **Saiko Berry said:**
> type 'gconftool-2 --recursive-unset /apps/panel' and press ENTER
type 'gnome-panel &' and press ENTER
Thanks, this worked.

---

### Post by Saiko Berry on 2010-01-04
No problem

---

