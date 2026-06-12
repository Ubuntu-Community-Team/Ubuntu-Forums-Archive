---
title: "openoffice2 and pyuno"
date: 2006-01-30
forum: General Help
---

### Post by andre77 on 2006-01-30
I have a problem with pyuno: if i try to import the module:

> andre@muletto:~$ python
Python 2.4.2 (#2, Sep 30 2005, 21:19:01)
[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pyuno
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
SystemError: dynamic module not initialized properly


Any idea?

---

### Post by waffen on 2006-05-04
Hello!

Recently I have the same trouble and I find the solution in this page: [http://www.ubuntuforums.org/showthread.php?t=122841&highlight=pyuno]("http://www.ubuntuforums.org/showthread.php?t=122841&highlight=pyuno")

You try this line only:

```
sudo ldconfig -v /usr/lib/openoffice2/program
```

And pyuno works fine!!

Good luck!!

---

### Post by elwood_j_blues on 2006-05-11
Thanks for this. It helps me a lot.

Interestingly, the "old" packages (release candidates) of OpenOffice.org2 seem to work out of the box, however the stable packages available through the apt repository

```
deb http://people.ubuntu.com/~doko/OOo2/ ./
```

seem to be broken and need your fix.

---

