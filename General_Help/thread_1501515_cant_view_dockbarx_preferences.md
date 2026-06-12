---
title: "cant view dockbarx preferences"
date: 2010-06-04
forum: General Help
---

### Post by rock4christ on 2010-06-04
I havent been able to view the preferences for over a month. I contacted M7S, a dockbar dev, and he said it was due to a bug that would be fixed in the latest version. when i ran dbx_preference.py then, i'd get:
Traceback (most recent call last):
File "/usr/bin/dbx_preference.py", line 1264, in <module>
PrefDialog()
File "/usr/bin/dbx_preference.py", line 793, in __init__
self.update()
File "/usr/bin/dbx_preference.py", line 975, in update
alpha = colors[a] * 256
KeyError: 'color1_alpha'

I did a complete removal and reinstall of the new version(although, it still remembers my pinned apps, so im prob missing a config file)
I now get:
progname=dbx_preference.py; RGBA=on
Traceback (most recent call last):
  File "/usr/bin/dbx_preference.py", line 959, in <module>
    PrefDialog()
  File "/usr/bin/dbx_preference.py", line 567, in __init__
    self.update()
  File "/usr/bin/dbx_preference.py", line 703, in update
    color = gtk.gdk.color_parse(self.globals.colors[c])
KeyError: 'color1'

and still no box when i right click and select properties

---

