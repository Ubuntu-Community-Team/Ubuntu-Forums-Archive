---
title: "/usr/lib/libxml2.so.2: undefined symbol: gzopen64"
date: 2010-11-07
forum: General Help
---

### Post by Veered on 2010-11-07
So, after installing ffmpeg I find that the python code below no longer works.


```
>>> from ctypes import *
>>> lib = cdll.LoadLibrary('/home/lucas/projects/LumenVoxClient/lvclient.so')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/var/django-stack/python/lib/python2.6/ctypes/__init__.py", line 431, in LoadLibrary
    return self._dlltype(name)
  File "/var/django-stack/python/lib/python2.6/ctypes/__init__.py", line 353, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: /usr/lib/libxml2.so.2: undefined symbol: gzopen64

```

No idea why. I have tried reinstalling zlib and libxml2.so.2 to no avail.

---

### Post by Veered on 2010-11-08
After much research I discovered that I needed to delete all of the libz.so files outside of /lib. In my case I had one in /usr/lib, and I also had a local application version (bitnami). After I deleted those, I ran ldconfig and waalaaaaaa!

---

