---
title: "was wondering if anyone know a few commands"
date: 2010-11-05
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-11-05
sometimes when i login a applet or two fails to load correctly or does not load at all so does anyone know a command to reload them
also sometimes my window border fails to load is there a command to reload just that part or do i have to keep reloading the entire window manager
is it possible to use the metacity window decorator and still use compiz? [[reference image]]("http://i51.tinypic.com/oqiolg.png")

---

### Post by janpol on 2010-11-05
In order to reload the applets, try:

```
killall gnome-panel
```

About using metacity, I think you can configure that using compiz manager. I'm at work (we use CentOS here without compiz xD) so I can't confirm that right now :p

Edit: I've found this (it's a little old but maybe it works for you)

[http://ubuntuforums.org/showthread.php?t=686345]("http://ubuntuforums.org/showthread.php?t=686345")

---

### Post by pqwoerituytrueiwoq on 2010-11-05
killall gnome-panel
worked thanks
edit: @ above edit if that is correct then compiz uses metacity's window decorator by default i thought compiz used a look alike window decorator

---

