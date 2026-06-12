---
title: "Compiz fade to desktop tweaks"
date: 2010-07-02
forum: General Help
---

### Post by J V on 2010-07-02
I have an interesting system... I don't have a desktop: Instead I replaced it with a maximized unmoveable all desktops bottom of the layers terminator window...

Problem is, when I hit Ctrl Alt D (To fade to desktop) Terminator also minimizes (Even though I set it to unminimizeable in window settings)

How do I exclude "class=Terminator" from the show desktop effect?

Found it: "gconftool-2 --type bool --set /apps/compiz/general/allscreens/options/hide_skip_taskbar_windows False"

---

