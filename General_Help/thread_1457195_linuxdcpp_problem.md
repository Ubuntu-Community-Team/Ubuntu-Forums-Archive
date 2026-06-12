---
title: "linuxdcpp problem"
date: 2010-04-18
forum: General Help
---

### Post by h3llb0y~ on 2010-04-18
whenever i start linuxdc++, it loads the user list really slowly and then just closes.....
i ran it through terminal and got this(it was repeated MANY times):

```
(linuxdcpp:3248): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
Segmentation fault

```

any idea what the problem seems to be?:confused:

---

