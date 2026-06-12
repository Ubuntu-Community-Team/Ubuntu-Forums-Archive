---
title: "Strange Gnome panel crash (Autohide)"
date: 2011-03-03
forum: General Help
---

### Post by An Sanct on 2011-03-03
Hello everyone!

I'm using Ubuntu Maverick and just a few minutes ago I checked "Autohide" in one of the panels properties, big mistake! The panel just crashes my OS from now on, disabling any clicking, Alt+F2, Alt+t and any other action in the GUI part. So I'm forced to Ctrl+Alt+F_, login and reboot.

Luckily I have a Live USB, so I can get on-line.

The main question here is: Where are the panel settings stored, so I can revert them?

---

### Post by Verbeck on 2011-03-03
i think its in ~/.gconf/apps/panel
so try[I]
```
rm -rf ~/.gconf/apps/panel/
pkill gnome-panel
``` [/I]to reset them to default

---

### Post by An Sanct on 2011-03-03
Thanks, that reset the whole thing for me :)

PS. And most importantly, now everything is working again...

---

