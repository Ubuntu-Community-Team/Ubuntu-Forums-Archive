---
title: "PyQt4: QtCore there, QtGui missing?"
date: 2010-12-29
forum: General Help
---

### Post by kernco on 2010-12-29
I just did
```
sudo apt-get install python-qt4
```
to install PyQt4, and while I can import the QtCore package, it can't seem to find the QtGui package.
```

Python 2.6.6 (r266:84292, Sep 15 2010, 15:52:39) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import PyQt4
>>> from PyQt4 import QtCore
>>> from PyQt4 import QtGui
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: cannot import name QtGui
>>> 

```
Is this a bug in the deb package? How can I fix it?

Ubuntu 10.10 32-bit

---

### Post by kernco on 2010-12-29
Ok, apparently my brother tried installing PyQt earlier by downloading it from the website and doing configure/make/install. I think that might be what's causing the problem. I can't figure out how to restore everything back to the package version, though. I did a purge and install of the package, but it's still not working.

---

