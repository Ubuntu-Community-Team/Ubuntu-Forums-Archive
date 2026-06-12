---
title: "desktop enviorment"
date: 2010-03-14
forum: General Help
---

### Post by joshbrice on 2010-03-14
how to start the desktop enviorment from the command line.

---

### Post by bruno9779 on 2010-03-14
If gnome:

```
sudo service gdm start
```

---

### Post by ibuclaw on 2010-03-14
A new X session?
```
startx
```

To instead start a DM
```
sudo start gdm
```
Replace "gdm" if needed.

Regards
Iain

---

