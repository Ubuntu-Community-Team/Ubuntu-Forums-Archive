---
title: "python help(&quot;modules&quot;) Seg fault - gtk"
date: 2011-11-25
forum: General Help
---

### Post by barr5790 on 2011-11-25
Hello - sorry if the solution to this problem is obvious - I will freely admit I am not the most competent linux user in the world.
I have recently started using xubuntu (11.10) which I quite like. I occasionally dabble in odd areas of programming and the only one which I can think would be relevant is opencv which I built somewhat recently - as it has gtk dependencies

In the python interpretor typing help("modules") produces the following:

>>> help("modules")

Please wait a moment while I gather a list of all available modules...

/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  from gtk import _gtk

** (python:8212): CRITICAL **: pyg_register_boxed: assertion `boxed_type != 0' failed
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: Warning: cannot register existing type `GdkDevice'
  from gtk import _gtk
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: Warning: g_type_get_qdata: assertion `node != NULL' failed
  from gtk import _gtkgtk-2.0/gtk/__init__.py:40: Warning: g_type_get_qdata: assertion `node != NULL' failed
  from gtk import _gtk
Segmentation fault

Previously gtk was spitting out the the error before the critical error line, even after opencv installation. The critical error /  seg fault are new and frankly rather irritating.

I assume its relevant - the line  from gtk import _gtk will execute without any error messages if I type it into the interpreter.

Any advice appreciated, especially advice which a non power user can comprehend.
Cheers.

---

### Post by Axed on 2011-12-20
This is a confirmed bug, see [https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/896836](https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/896836)

---

