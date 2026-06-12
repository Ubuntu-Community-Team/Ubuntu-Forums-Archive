---
title: "Not able to use Tkinter"
date: 2012-04-15
forum: General Help
---

### Post by Sammax on 2012-04-15
while trying to import i get the following message.........pls help.......




Traceback (most recent call last):
  File "hello.py", line 1, in <module>
    from Tkinter import *
  File "/usr/lib/python2.7/lib-tk/Tkinter.py", line 42, in <module>
    raise ImportError, str(msg) + ', please install the python-tk package'
ImportError: No module named _tkinter, please install the python-tk package

---

### Post by memilanuk on 2012-04-15
so... did you do what it told you to do? ;)

tkinter is split off into a separate package from the main python install; you have to explicitly install python-tk in order to develop tkinter programs.

P.S. probably a question better asked in the Programming sub-forum...

---

### Post by Thewhistlingwind on 2012-04-15
```
sudo apt-get install python-tk

```
Notice that it explicitly instructs you to install python-tk in the error message. ;)

---

### Post by Sammax on 2012-04-16
trying to install gives:

Package python-tk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-tk' has no installation candidate

---

### Post by locomonkey on 2012-07-07
If you are trying to use Python 3.x, the package you need is python3-tk.
So:

```
$ sudo apt-get install python3-tk
```

Hope it helps!

---

