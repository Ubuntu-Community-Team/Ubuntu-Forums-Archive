---
title: "No gnome panels are loaded."
date: 2011-01-03
forum: General Help
---

### Post by karthick87 on 2011-01-03
After a poweroff,i have restarted my system.It loads all the desktop icons but no panels were there..Also i cant click on any icons in my desktop.Hitting ALT+F2 is also not working..Can anyone help me??

---

### Post by karthick87 on 2011-01-03
Bump...

---

### Post by matt_symes on 2011-01-03
Hi

Press ctrl + atl + T to get a terminal. Does

```
ps aux | grep gnome-panel
```

show any running panels?

Are any errors displayed if you type

```
gnome-panel
```

You might try deleting (or renaming < i would rename>) your gnome directories in your home directory. They should get regenerated.

These are .gnome2, .gconf, .gconfd, .gnome2_private and maybe some others. I can never remember.

Kind regards

---

