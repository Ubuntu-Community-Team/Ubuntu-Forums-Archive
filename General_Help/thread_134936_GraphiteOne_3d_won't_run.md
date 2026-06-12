---
title: "GraphiteOne 3d won't run"
date: 2006-02-22
forum: General Help
---

### Post by dalani on 2006-02-22
I installed the GraphiteOne3d package in Ubuntu 5.04 Hoary and the following error when run:

```
@ubuntu:~$ graphiteone
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteonesplashscreen.py", line 16, in ?
    from qt import Qt
  File "/opt/GraphiteOne/lib/qt.py", line 46, in ?
    import libsip
ImportError: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
/opt/GraphiteOne/lib/HPY.py:2: RuntimeWarning: Python C API version mismatch for module HPYc: This Python has API version 1012, module HPYc has version 1011.
  import HPYc
Traceback (most recent call last):
  File "/opt/GraphiteOne/lib/graphiteone.py", line 15, in ?
    from graphiteoneapplication import GOneApplication
  File "/opt/GraphiteOne/lib/graphiteoneapplication.py", line 17, in ?
    from qt import QString
  File "/opt/GraphiteOne/lib/qt.py", line 46, in ?
    import libsip
ImportError: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

It seems to be a libs version mismatch but GraphiteOne docs list Python2.2 and libsstdc 2.9 as the only earliest version requirements. Hoary has Python2.4 nd libs**v3. So why the error message??? any help would be appreciated

---

