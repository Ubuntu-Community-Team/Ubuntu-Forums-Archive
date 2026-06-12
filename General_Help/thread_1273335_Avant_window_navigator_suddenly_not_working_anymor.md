---
title: "Avant window navigator suddenly not working anymore"
date: 2009-09-23
forum: General Help
---

### Post by malanco on 2009-09-23
hi guys, yesterday after i did a reboot of my pc AWN is not loading anymore, can u help a little here?, here's the output of the terminal

agustin@agustin-laptop:~$ avant-window-navigator
Traceback (most recent call last):
  File "/usr/bin/awn-applets-migration", line 21, in <module>
    import awn
  File "/usr/lib/python2.6/dist-packages/awn/__init__.py", line 25, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.6/gtk-2.0/gobject/__init__.py", line 54, in <module>
    from gobject.constants import *
  File "/var/lib/python-support/python2.6/gtk-2.0/gobject/constants.py", line 24, in <module>
    import gobject._gobject
ImportError: No module named _gobject


my current kernel is :

agustin@agustin-laptop:~$ uname -r
2.6.28-11-generic

thanks!!

---

### Post by malanco on 2009-09-24
bump any1?? :(

---

