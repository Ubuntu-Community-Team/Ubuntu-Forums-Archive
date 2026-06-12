---
title: "wxbanker not working in lucid."
date: 2010-11-16
forum: General Help
---

### Post by karthick87 on 2010-11-16
I have installed wxbanker in lucid,but its not getting open.When i type **wxbanker **in terminal,its giving the following error.

```
karthick@Ubuntu-desktop:~$ wxbanker
Traceback (most recent call last):
  File "/usr/bin/wxbanker", line 2, in <module>
    from wxbanker.main import main
  File "/usr/lib/python2.6/dist-packages/wxbanker/main.py", line 32, in <module>
    import wx, wx.aui
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
ImportError: /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core_.so: symbol _ZN12wxSizerFlags24ReserveSpaceEvenIfHiddenEv, version WXU_2.8.8 not defined in file libwx_gtk2u_core-2.8.so.0 with link time reference

```

---

### Post by midtown on 2010-11-17
Wow, that's a crazy one! Can you please file a bug via "ubuntu-bug wxbanker". That may require 0.8.2 from the PPA to work, but it would provide some valuable information.

It appears to be a wxPython issue though, do you happen to know if it was installed before or if anything is special about your setup.

Thanks!

---

### Post by karthick87 on 2010-11-17
I have filed a bug report.

---

