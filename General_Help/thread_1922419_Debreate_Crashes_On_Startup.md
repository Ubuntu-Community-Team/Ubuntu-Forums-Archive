---
title: "Debreate Crashes On Startup"
date: 2012-02-08
forum: General Help
---

### Post by MrBandicootKid on 2012-02-08
I wanted to make a Debian package and got this program called Debriate. The problem is that the program crashes when it's finished loading. How do I stop this?

---

### Post by TeoBigusGeekus on 2012-02-09
Start it from a terminal - probably with
```
debreate
```
and post us any error messages.

---

### Post by droidjustin on 2012-04-02
I am trying to get debreate to start when ever I put debreate in the terminal i get the following error

```
Traceback (most recent call last):
  File "/usr/bin/debreate", line 12, in <module>
    import wx, sys, os, debreate, db, language, shutil
  File "/usr/share/debreate/debreate.py", line 23, in <module>
    import os, sys, wx.lib.dialogs, db, webbrowser, language, shutil, subprocess
  File "/usr/share/debreate/db.py", line 5, in <module>
    import wx, wx.combo, wx.lib.mixins.listctrl as LC, os, sys, language
ImportError: No module named combo


```
thank you

---

### Post by rolo2255 on 2012-04-03
For me this problem was solved typing:
sudo apt-get install python-wxgtk2.8
I run under lucid linx  x64

---

### Post by FerNamib on 2012-11-02
Thanks. Installing python-wxgtk2.8 worked for me too. Going on with Debreate.

---

