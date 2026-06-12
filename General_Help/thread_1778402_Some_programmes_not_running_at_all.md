---
title: "Some programmes not running at all"
date: 2011-06-09
forum: General Help
---

### Post by thameera on 2011-06-09
I installed Ubuntu and switched to the pure LXDE desktop. Now some programmes don't run when I click on them in the Applications menu. For example gpodder doesn't run and when I type gpodder in the terminal, the following warnings appear:
```
(process:6115): Gtk-WARNING **: Locale not supported by C library.
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

What's wrong with my system?

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **thameera said:**
> I installed Ubuntu and switched to the pure LXDE desktop. Now some programmes don't run when I click on them in the Applications menu. For example gpodder doesn't run and when I type gpodder in the terminal, the following warnings appear:
```
(process:6115): Gtk-WARNING **: Locale not supported by C library.
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

```What's wrong with my system?

I wouldn't use just pure LXDE.. 
You can install lubuntu-desktop and this shouldn't happen. 

Just a suggestion.  There maybe a work-around... but I had plenty of issues going the route you have gone to install that environment before.  It's better to use lubuntu session verses lxde in my experience. :)

lubuntu would be essentially the exact same thing, but it works better. :)

---

### Post by thameera on 2011-06-09
Well, it is 'lubuntu-desktop' I've installed. :S

---

### Post by thameera on 2011-06-09
Anyone?

---

