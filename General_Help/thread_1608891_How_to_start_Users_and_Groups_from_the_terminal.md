---
title: "How to start Users and Groups from the terminal?"
date: 2010-10-29
forum: General Help
---

### Post by Quackers on 2010-10-29
I'm troubleshooting. Users and Groups will not run from the System > Admin menu. It starts but after 10 seconds it disappears from the bottom panel. No GUI appears. Thanks.

---

### Post by 666f6f on 2010-10-29
Hi there,

You can start Users and Groups from the terminal using the following command ```
users-admin
```.

The *Users and Groups* program is found in the gnome-system-tools package (at least in Maverick!).

---

### Post by Quackers on 2010-10-29
Thanks 666f6f I did use sudo users-admin and that's giving me

```
GLib-GIO-ERROR **: Settings schema 'org.gnome.system-tools.users' is not installed

aborting...
Trace/breakpoint trap
```

---

