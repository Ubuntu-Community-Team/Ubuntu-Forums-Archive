---
title: "Sage syntax error on startup"
date: 2010-04-28
forum: General Help
---

### Post by Dorsenstein on 2010-04-28
I recently installed the package 'sagemath' on Ubuntu 9.10 Karmic without any errors by typing:
```

sudo apt-get install sagemath
```However, whenever I type the command 'sage' and press enter, this happens


```
/usr/lib/sagemath/local/lib/python/site.py:150: Warning: 'with' will become a reserved keyword in Python 2.6
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/lib/sagemath/local/bin/sage-location", line 3, in <module>
    import os
  File "/usr/lib/sagemath/local/lib/python/os.py", line 758
    bs = b""
           ^
SyntaxError: invalid syntax
/usr/lib/sagemath/local/lib/python/site.py:150: Warning: 'with' will become a reserved keyword in Python 2.6
'import site' failed; use -v for traceback
/usr/lib/sagemath/local/lib/python/site.py:150: Warning: 'with' will become a reserved keyword in Python 2.6
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/lib/sagemath/local/bin/sage-ipython", line 10, in <module>
    import IPython
ImportError: No module named IPython
Traceback (most recent call last):
  File "/usr/lib/sagemath/local/bin/sage-cleaner", line 21, in <module>
    import os, shutil, sys, time, socket
  File "/usr/lib/sagemath/local/lib/python/os.py", line 758
    bs = b""

```I even tried uninstalling and reinstalling the package but to no avail.

Any help would be much appreciated, thanks!

---

### Post by GrosPatapouf on 2010-04-29
Try to install python-2.4 (with dev and dbg package).
add export PYTHONPATH=/usr/lib/python2.4 in the .bashrc file (in your home dir), then relaunch a terminal.

---

### Post by Dorsenstein on 2010-05-01
I tried this with both python 2.4 and 2.6, though sage still doesn't work. I have IPython installed, even though sage says the module is missing...

---

### Post by gmargo on 2010-05-04
I installed sagemath on 9.10 karmic (32-bit), but I don't see any problem. I do not have a 
/usr/lib/sagemath/local/lib/python/ directory or any files under it.  You have a site.py file at least.  Where did that come from, and what's in it?

---

### Post by haraldschilly on 2010-05-05
> **Dorsenstein said:**
> I recently installed the package 'sagemath' on Ubuntu 9.10 Karmic without any errors by typing:
```

sudo apt-get install sagemath
```

The sagemath debian package is years old, was never updated and no longer supported. You should download the official precompiled binary from [http://www.sagemath.org]("http://www.sagemath.org").

H

---

