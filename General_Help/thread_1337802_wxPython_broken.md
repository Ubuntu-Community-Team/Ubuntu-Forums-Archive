---
title: "wxPython broken?"
date: 2009-11-25
forum: General Help
---

### Post by genjix on 2009-11-25
```

genjix@l:~$ python
Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41)
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import wx
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
ImportError: /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core_.so: symbol _ZN12wxSizerFlags24ReserveSpaceEvenIfHiddenEv, version WXU_2.8.8 not defined in file libwx_gtk2u_core-2.8.so.0 with link time reference
>>>

genjix@l:~$ ldd /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core_.so | grep -i wx_gtk2u_core
        libwx_gtk2u_core-2.8.so.0 => /usr/lib/libwx_gtk2u_core-2.8.so.0 (0xb7762000)

```

Not sure what's wrong here :p

---

### Post by genjix on 2009-11-25
needed to install:
libwxgtk2.8-dev

then works!

---

### Post by wwood on 2010-09-06
Thanks.

---

