---
title: "Issue with locales"
date: 2011-07-17
forum: General Help
---

### Post by ushills on 2011-07-17
Hi, seem to be getting a few of this issue with a number of applications, think that there is an issue with my locales but can't seem to fix it.

Any ideas

```
gpodder

(process:32089): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/gpodder", line 201, in <module>
    from gpodder import gui
  File "/usr/lib/pymodules/python2.7/gpodder/gui.py", line 71, in <module>
    from gpodder import util
  File "/usr/lib/pymodules/python2.7/gpodder/util.py", line 69, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.7/locale.py", line 531, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```

---

