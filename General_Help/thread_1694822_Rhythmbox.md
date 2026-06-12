---
title: "Rhythmbox"
date: 2011-02-24
forum: General Help
---

### Post by Kanga on 2011-02-24
I typed rhythmbox in terminal, and this is the output:

(rhythmbox:4146): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)

Does anyone understand this?

Rhythmbox opened and it had all my music, so how do i get it back to show under Applications/ Sound and video?

---

### Post by 3rdalbum on 2011-02-24
> **Kanga said:**
> I typed rhythmbox in terminal, and this is the output:

(rhythmbox:4146): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)

Does anyone understand this?

Rhythmbox opened and it had all my music, so how do i get it back to show under Applications/ Sound and video?

The error message is meaningless, pretty much. Lots of Gnome programs generate those messages even when everything is fine.

Right-click the Applications menu and go to Edit Menu, then you can either create a new Rhythmbox launcher or check that your original launcher is hidden (unticked).

---

### Post by Kanga on 2011-02-25
Thank you 3rdalbum,

managed with a bit of searching to find Rhythmbox command line to reinstall it in Applications.
The joys of Linux:D

---

