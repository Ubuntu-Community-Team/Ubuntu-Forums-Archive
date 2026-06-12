---
title: "How do i reset or add a panel"
date: 2009-07-14
forum: General Help
---

### Post by Ayeco on 2009-07-14
I left my friend alone with my computer for 2 minutes, and somehow he managed to drag all 4000 of my songs to my panel.  Now when i try to click applications or anything, it opens a song icon that is behind the applications icon. This was my only panel, so how do i reset this panel or create a new one from the terminal or gconf? thanks

---

### Post by drs305 on 2009-07-14
You can return a panel to the defaults by running the following command (If you can't get to a menu to open a terminal, use ALT-F2):
```

gconftool-2 --recursive-unset /apps/panel && killall gnome-panel 

```

The first command will reset the panels to the default settings, the second refreshes the panels.

---

