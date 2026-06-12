---
title: "Problem at top panel"
date: 2010-08-15
forum: General Help
---

### Post by RooSH23 on 2010-08-15
Hi everyone.
I've just installed ubuntu 10.04.
every time i log in the icons at the top panel appear to change their position (plz take a look at the screenshot attached).
My question is how can i change it back to the default.

---

### Post by howefield on 2010-08-15
You can right click each applet and uncheck Lock to Panel, then move into position and then Lock to Panel again, or reset your panels by opening a terminal and paste in the following 3 commands, one at a time.

```
gconftool-2 --shutdown
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

---

