---
title: "power manager warning in ~/.xsession-errors"
date: 2011-04-20
forum: General Help
---

### Post by AnotherMuggle on 2011-04-20
I am getting the following error in my ~/.xsession-errors log file every minute or so.  Can anyone offer me any guidance on what might be causing the problem?

```
(gnome-power-manager:1646): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
```

Cheers,
Tom

---

