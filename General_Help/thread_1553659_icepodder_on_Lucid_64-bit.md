---
title: "icepodder on Lucid 64-bit"
date: 2010-08-15
forum: General Help
---

### Post by r_avital on 2010-08-15
Hello,

Trying to install icepodder on Lucid 64-bit, I don't have any "architecture" problems of any kind.  Running icepodder from a terminal, I do get the splash-screen for a short time, then the following output:

```
CastPodderGui.py:48: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from   wxPython.wx import *
/usr/share/icepodder/ipodder/core.py:31: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  from   sha import *
xmms couldn't be imported
Beep-Media-Player couldn't be imported
/usr/share/icepodder/ipodder/history.py:23: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import logging,md5,time,os,threading,time
Traceback (most recent call last):
  File "CastPodderGui.py", line 3623, in <module>
    main()
  File "CastPodderGui.py", line 3617, in main
    myApp = iPodderGui(ipodder)
  File "CastPodderGui.py", line 685, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib64/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7978, in __init__
    self._BootstrapApp()
  File "/usr/lib64/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 7552, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "CastPodderGui.py", line 1519, in OnInit
    self.InitHooks()
  File "CastPodderGui.py", line 1876, in InitHooks
    for att, method in inspect.getmembers(self, inspect.ismethod): 
  File "/usr/lib/python2.6/inspect.py", line 252, in getmembers
    value = getattr(object, key)
  File "/usr/lib64/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 9619, in GetAcceleratorTable
    return _core_.Window_GetAcceleratorTable(*args, **kwargs)
TypeError: in method 'Window_GetAcceleratorTable', expected argument 1 of type 'wxWindow *'

```I have compiled/installed it from the source code.  I have satisfied the following dependencies:
python 
libwxgtk 2.8 
python-wxgtk 2.8 
id3v2  
python-libxml2 

Any ideas?  Anyone?

---

### Post by r_avital on 2010-09-30
bump

---

