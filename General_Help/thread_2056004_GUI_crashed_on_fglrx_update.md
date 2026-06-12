---
title: "GUI crashed on fglrx update"
date: 2012-09-10
forum: General Help
---

### Post by Zvlwab on 2012-09-10
There was a fglrx-updates update yesterday. Since I updated that package my graphics are very bugged.
On my laptop I was able to fix it by purging fglrx-updates and installing fglrx.

On my pc that didn't work at all. I'm able to use it by purging all fglrx packages. But now I can't use dual screen anymore, because when I run arandr I get the following:
```
Traceback (most recent call last):
  File "/usr/bin/arandr", line 25, in <module>
    main()
  File "/usr/lib/pymodules/python2.7/screenlayout/gui.py", line 302, in main
    force_version=options.force_version
  File "/usr/lib/pymodules/python2.7/screenlayout/gui.py", line 143, in __init__
    self.filetemplate = self.widget.load_from_x()
  File "/usr/lib/pymodules/python2.7/screenlayout/widget.py", line 77, in load_from_x
    self._xrandr.load_from_x()
  File "/usr/lib/pymodules/python2.7/screenlayout/xrandr.py", line 134, in load_from_x
    o.modes.append(Size(int(a) for a in d.strip().split(" ")[0].split("x")))
  File "/usr/lib/pymodules/python2.7/screenlayout/auxiliary.py", line 37, in __new__
    arg = tuple(arg)
  File "/usr/lib/pymodules/python2.7/screenlayout/xrandr.py", line 134, in <genexpr>
    o.modes.append(Size(int(a) for a in d.strip().split(" ")[0].split("x")))
ValueError: invalid literal for int() with base 10: '1080i'
```

Is anyone else having this problem? Please help me

---

