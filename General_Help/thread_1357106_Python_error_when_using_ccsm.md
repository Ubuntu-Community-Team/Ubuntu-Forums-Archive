---
title: "Python error when using ccsm"
date: 2009-12-16
forum: General Help
---

### Post by PinkFloyd102489 on 2009-12-16
> 
brandon@brandon-karmic-vm:~$ ccsm
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 8, in <module>
    import CommandNotFound
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/__init__.py", line 1, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/CommandNotFound.py", line 5, in <module>
    from util import gettext_wrapper as _
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/util.py", line 5, in <module>
    import gettext
EOFError: EOF read where object expected
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
ValueError: bad marshal data

Original exception was:
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 8, in <module>
    import CommandNotFound
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/__init__.py", line 1, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/CommandNotFound.py", line 5, in <module>
    from util import gettext_wrapper as _
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/util.py", line 5, in <module>
    import gettext
EOFError: EOF read where object expected


When I try to run ccsm from the command line, I get that error. Also when I try to update to Python 3.1, I get the same.

Ideas? Im on 9.10 Karmic with Python version 2.6.4.

---

