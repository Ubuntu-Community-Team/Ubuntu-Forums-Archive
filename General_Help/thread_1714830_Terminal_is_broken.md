---
title: "Terminal is broken"
date: 2011-03-25
forum: General Help
---

### Post by Giraffro on 2011-03-25
When I run terminal I just get the flashing cursor box; no prompt loads and I can't run commands. This only happens in one of my login accounts. I've tried reinstalling gnome-terminal, but to no avail.

Any suggestions?

---

### Post by Krytarik on 2011-03-25
Try resetting its settings:
- press Alt+F2
- enter this command:
```
gconftool-2 --recursive-unset /apps/gnome-terminal
```

---

### Post by Giraffro on 2011-03-25
Defaulted my colour scheme but still doesn't load. :/

---

### Post by wojox on 2011-03-25
Go to /etc/skel and copy the bash files to your home.

---

### Post by Giraffro on 2011-03-25
Done. Thanks!

---

