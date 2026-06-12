---
title: "Python and pygtk issue"
date: 2010-07-15
forum: General Help
---

### Post by rdnrvn on 2010-07-15
Hi,

I installed pygtk recently and also the latest version of Python. The problem is pygtk got installed for python2.5 and not the latest version , 2.6

That is, when I run a python program, say,
python test.py

This is the output:
Traceback (most recent call last):
  File "test.py", line 5, in <module>
    import pygtk
ImportError: No module named pygtk


But if i run: python2.5 test.py, everything runs fine.

How can I sort this issue? I want pyGTK to be available to the default python.

Thanks!

---

