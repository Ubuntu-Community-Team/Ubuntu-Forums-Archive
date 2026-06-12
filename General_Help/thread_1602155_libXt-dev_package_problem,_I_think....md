---
title: "libXt-dev package problem, I think..."
date: 2010-10-21
forum: General Help
---

### Post by ladasky on 2010-10-21
Hi there, I'm tearing my hair out trying to solve a package dependency problem.  I'm running Karmic.
 
I'm trying to make use of a non-canonical package called [pymacs]("http://wwwuser.gwdg.de/~dseelig/pymacs.html").  This isn't the interface between EMACS and Python, it's an interface between Python and GROMACS.  Wouldn't you know it, the Linux universe is so dense with software that the same name got used twice.
 
Anyway, I've installed pymacs and tried to import it from my Python interpreter.  Here's what I get:
 
```
IDLE 2.6.4      ==== No Subprocess ====
>>> from pymacs import *
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    from pymacs import *
  File "/usr/local/lib/python2.6/dist-packages/pymacs/__init__.py", line 23, in <module>
    from molecule import *
  File "/usr/local/lib/python2.6/dist-packages/pymacs/molecule.py", line 37, in <module>
    from atomselection import *
  File "/usr/local/lib/python2.6/dist-packages/pymacs/atomselection.py", line 24, in <module>
    import _pymacs
ImportError: /usr/local/lib/python2.6/dist-packages/pymacs/_pymacs.so: undefined symbol: XtManageChild
```
 
I've never received a build-style error message from inside a Python import call before.
 
I went searching for information on the XtManageChild function, and trust me, that wasn't as easy to find as I would have hoped.  My best bet in the past has been to go a Google search in packages.ubuntu.com using the function name as the search term.  XtManageChild appears in the search, in the filelist of package libxt-dev, for [Hardy]("http://packages.ubuntu.com/hardy/i386/libxt-dev/filelist") and for [Lucid]("http://packages.ubuntu.com/lucid/i386/libxt-dev/filelist") -- but not for Karmic.

I don't know why Google doesn't turn up [http://packages.ubuntu.com/karmic/i386/libxt-dev/filelist](http://packages.ubuntu.com/karmic/i386/libxt-dev/filelist), but I guessed at it after seeing the names of the other two web pages, and it exists, and it too lists XtManageChild.
 
I checked my manifest of installed packages on Karmic.  I already had libxt-dev installed.  I tried reinstalling it in case it got corrupted somehow.  This did not fix the error.

Any advice would be appreciated!  Thanks!

---

