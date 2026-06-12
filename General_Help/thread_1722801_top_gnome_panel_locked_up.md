---
title: "top gnome panel locked up"
date: 2011-04-06
forum: General Help
---

### Post by LewRockwellFAN on 2011-04-06
I was adding the Force-application-to-quit doodad to my top gnome panel and something fell on my kb and suddenly it was chock full of multiple copies of it. Now all the other launchers and whatnots have dissapeared and the Applications, Places, and System menus can't be opened. If I click on them I just launch Force-quit. So I can't get a command line, I can't open Synaptic, I can't launch a file browser, and I can't start a web browser. I've spent a long time deleting the icons but they don't move and the visible number doesn't change. Maybe every time I delete one the total goes down from an astronomical number to an astromical number - 1 and most remain invisible or maybe I'm not really deleting anything. So all the obvious ways are out. Two approaches occur to me but I don't know how to implement them.
1. Maybe I can boot from another partition, as I'm doing now, and edit something or delete something in the one that's borked. But what?
2. Maybe there is some other way of launching a terminal? Some magic hot key combination, maybe that works at just the right during boot? If there is maybe I could google up some commands to solve the problem.

Not all that keen on doing another install and I haven't backed up that partition, but if that's the only way I will.

Any ideas?

---

### Post by ~Plue on 2011-04-06
you could reset the panels to default by running the following from a terminal (ctrl+alt+T), run dialog (alt+F2) or a virtual console (ctrl+alt+F1 - F6)
```
gconftool-2 --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
killall gnome-panel[COLOR=#FF0000][B][I][FONT=Verdana]
[/FONT][/I][/B][/COLOR]
```[COLOR=#ff0000][B][I][FONT=Verdana]
[/FONT][/I][/B][/COLOR]-hope this helps[COLOR=#ff0000][B][I][FONT=Verdana]
[/FONT][/I][/B][/COLOR]

---

### Post by LewRockwellFAN on 2011-04-06
Thanks. That's perfect.

---

