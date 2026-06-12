---
title: "wammu start problem"
date: 2011-10-07
forum: General Help
---

### Post by x53x6ex69x67x67x65x72 on 2011-10-07
Hi 
I'm using Ubuntu 10.04 (Lucid Lynx) 
I installed wammu from ubuntu repositories but when I try to start it it gives this errors:
```
Traceback (most recent call last):
  File "/usr/bin/wammu", line 31, in <module>
    import Wammu.Locales
  File "/usr/lib/pymodules/python2.6/Wammu/Locales.py", line 31, in <module>
    import wx
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 14774, in <module>
    from _misc import *
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_misc.py", line 4, in <module>
    import _misc_
ImportError:  /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_misc_.so:  symbol _ZN7wxSound6CreateEiPKh, version WXU_2.8 not defined in file  libwx_gtk2u_adv-2.8.so.0 with link time reference

```
What's the problem?
How can i fix it?

Thanks

---

### Post by ario on 2011-10-07
Just 32 minutes after you, I got the same problem!!! :D I don't khow how to solve it;) Anyone khows?

---

### Post by x53x6ex69x67x67x65x72 on 2011-10-09
Hi 
I fixed it by removing "python-wxgtk2.8" & reinstalling "python-wxgtk2.6".

Thanks

---

