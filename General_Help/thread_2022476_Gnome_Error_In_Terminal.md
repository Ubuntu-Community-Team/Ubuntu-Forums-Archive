---
title: "Gnome Error In Terminal"
date: 2012-07-11
forum: General Help
---

### Post by Dgameman1 on 2012-07-11
Everytime I open something up in terminal
I get this error
```
(gnome-session-properties:16415): GLib-GObject-WARNING **: g_object_set_valist: object class `GsmAppDialog' has no property named `allow-shrink'

```

What do I do?

---

### Post by MG&amp;TL on 2012-07-11
It's a program bug in gnome-session-properties, and not a harmful one as far as I can tell.

Does it stop you doing anything? I personally would just ignore it.

I believe the program is trying to set the 'allow-shrink' property of a program, but that program doesn't have that property. Not harmful, as far as I know.

---

