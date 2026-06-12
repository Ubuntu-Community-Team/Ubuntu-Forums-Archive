---
title: "XGL/Compiz and wobbly menus"
date: 2006-06-17
forum: General Help
---

### Post by Neo Ex on 2006-06-17
Hi. Is there a way to remove the wobble from the menus? I use KDE and the wobbly here isn't so good like the one with GTK apps.
Thanks.

---

### Post by olsonar on 2006-06-17
launch gset-compiz and uncheck wobbly.

---

### Post by panurge77 on 2006-06-17
gconf-editor> apps > compiz > plugins > wobbly > screen0 > options
remove the "Unkown" key from map_windows_types

---

### Post by Neo Ex on 2006-06-18
Thank you! That worked! :D

---

