---
title: "WxPython"
date: 2006-03-25
forum: General Help
---

### Post by yootje on 2006-03-25
I tried to install WxPython, so I installed python-wxgtk2.6. I'm a total noob of Python.

I use the following script:

```

from wxPython.wx import *

class MyApp(wxApp):
    def OnInit(self):
        frame = wxFrame(NULL, -1, "Hello from wxPython")
        frame.Show(true)
        self.SetTopWindow(frame)
        return true

app = MyApp(0)
app.MainLoop()

```

But when I try to run it (python wx.py) I get

```
Traceback (most recent call last):
  File "wx.py", line 1, in ?
    from wxPython.wx import *
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wxPython/__init__.py", line 10, in ?
    import _wx
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wxPython/_wx.py", line 3, in ?
    from _core import *
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wxPython/_core.py", line 15, in ?
    import wx._core
  File "/home/yorian/documenten/dev/py/wx.py", line 1, in ?
    from wxPython.wx import *
ImportError: No module named wx

```

What's wrong? I already tried to install anything that looks like wx.

---

### Post by yootje on 2006-03-25
Kick.

---

### Post by kuerbt on 2006-06-07
apt-get install python-wxgtk2.6

---

### Post by stani on 2006-07-18
You've probably looked at old documentation or tutorial. Never use:

```
from wxPython.wx import *
```

but

```
import wx
```

So your code should probably be (did not check):
```
import wx

class MyApp(wx.App):
    def OnInit(self):
        frame = wx.Frame(None, -1, "Hello from wxPython")
        frame.Show(True)
        self.SetTopWindow(frame)
        return True

app = MyApp(0)
app.MainLoop()
```

Notice
- NULL -> None
- true -> True (Python is case sensitive)

Read also my [howto install latest wxPython & SPE (Feature rich Python IDE)]("http://www.ubuntuforums.org/showthread.php?t=218001&highlight=wxpython").

---

