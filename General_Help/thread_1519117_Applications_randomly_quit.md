---
title: "Applications randomly quit"
date: 2010-06-27
forum: General Help
---

### Post by dv3500ea on 2010-06-27
Lots of applications inexplicably quit. When run from the terminal there is always this error message given:
```
fatal error: Failed to register GObject with DBusConnection

```
Does anyone know of a way to fix this?

---

### Post by talon314 on 2010-06-28
I'm having the same issue with certain applications. Not sure how to go about finding a solution.

---

### Post by talon314 on 2010-06-29
Apparently it has something to do with updates to either libdbusmenu-glib1 or libdbusmenu-gtk1, I'm not sure which. Downgrading both of them brought pidgin back for me.

---

### Post by ghettowarrior on 2010-06-29
thanks,..

the problem is..

libdbusmenu-gtk1

after forcing the older version things work again.

greetings

---

### Post by dv3500ea on 2010-06-30
Thanks, that works. For reference, because it took a while for me to work out how to do so, to downgrade select the package in Synaptic Package Manager and click packages -> force version in the menu.

---

