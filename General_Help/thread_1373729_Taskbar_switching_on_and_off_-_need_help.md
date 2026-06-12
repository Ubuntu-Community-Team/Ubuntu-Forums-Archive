---
title: "Taskbar switching on and off - need help"
date: 2010-01-06
forum: General Help
---

### Post by antiphatique on 2010-01-06
Dear all,

I am a new Ubuntu user (three months so far on Karmic amd64, and very happy with my new OS). I had to do a force shutdown after a system freeze (while viewing video on my tv - dual display - with vlc). Upon restart, I noticed the network connection icon missing from the taskbar; there was an empty "slot" between the evolution and sound icons so I figured the network icon was simply not appearing correctly. I right clicked in that empty "slot" and chose to remove from taskbar with the intention of putting it back. After clicking remove, the taskbar started a cycle of constant disappear and reappear (about one second between each). The cycle is too fast to allow navigating in menus but I can access the terminal. Being new and all, I don't know how to configure the taskbar through the terminal... can someone help me fix my taskbar in the terminal? I hope to avoid restarting an install from scratch...

Thanks

---

### Post by antiphatique on 2010-01-10
I managed to restore the panels back to their default settings and therefore solve the problem. Three easy steps in terminal:

1: gconftool --recursive-unset /apps/panel
2: rm -rf ~/.gconf/apps/panel
3: pkill gnome-panel

Voilà!

---

