---
title: "GLib-GObject-CRITICAL"
date: 2012-02-29
forum: General Help
---

### Post by devendram on 2012-02-29
Hi,
       I am using ubuntu 11.10, I am getting following error in xsession-errors file.
GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

Size of xession-errors file is increasing every second. Anyone faced same problem ?

---

### Post by TeoBigusGeekus on 2012-02-29
Does it happen when running a particular app or randomly?

---

### Post by theInFan on 2012-04-20
I'm having this same issue with nautilus.
I've got a Windows 7/Oneiric dual-booted laptop. Oneiric installed via wubi.

Currently, the issue occurs every time I boot Ubuntu.
When I log in, the global menu and sidebar launcher load, but the sidebar won't autohide and all desktop icons are missing.
Additionally, Finder windows won't open and desktop context menu doesn't work.

I was able to temporarily fix the problem by running this in terminal:
```
ps -ewwo pid,args | nautilus
```When executed, everything returns to normal. Until that terminal window is closed.

If I change the arguments I get this:
```
Traceback (most recent call last):
   File "/usr/lib/python2.7/dist-packages/gi/__init__.py", line 23, in <module>
      from ._gi import _API, Repository
ImportError: could not import gobject (error was: ImportError('When using gi.repository
you must import static modules like "gobject". Please change all occurrences
of "import gobject" to "from gi.repository import GObject".',))

(nautilus:2529): Nautilus-Python-WARNING **: nautilus_python_init_python failed
Trackback (most recent call last):
   File "/usr/share/nautilus-python/extensions/nautilus_terminal.py", line 49, in <module>
      from gi.repository import GObject, Nautilus, Gtk, Gdk, Vte, GLib
   File "/usr/lib/python2.7/dist-packages/gi/__init__.py", line 23, in <module> 
      from ._gi import _API, Repository
ImportError: cannot import name _API
Segmentation Fault
```

---

