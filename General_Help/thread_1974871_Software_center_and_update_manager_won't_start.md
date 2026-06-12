---
title: "Software center and update manager won't start"
date: 2012-05-06
forum: General Help
---

### Post by glasafmt on 2012-05-06
Hi

I'm using Ubuntu Studio (based on ubuntu 11.04) and I can't get the software center or the upgrade manager to start.  If I open the software center from the command line, I get this error:

```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 111, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 40, in <module>
    from softwarecenter.db.application import Application, DebFileApplication
  File "/usr/share/software-center/softwarecenter/db/application.py", line 19, in <module>
    from apt.debfile import DebPackage
  File "/usr/lib/python2.7/dist-packages/apt/__init__.py", line 24, in <module>
    from apt.package import Package
  File "/usr/lib/python2.7/dist-packages/apt/package.py", line 42, in <module>
    import apt.progress.text
  File "/usr/lib/python2.7/dist-packages/apt/progress/__init__.py", line 32, in <module>
    from apt.progress.old import (CdromProgress, DpkgInstallProgress,
  File "/usr/lib/python2.7/dist-packages/apt/progress/old.py", line 35, in <module>
    from apt.progress import base, text
ValueError: bad marshal data (unknown type code)
```


and a very similar error when I try the update manager:

```
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 40, in <module>
    import apt
  File "/usr/lib/python2.7/dist-packages/apt/__init__.py", line 24, in <module>
    from apt.package import Package
  File "/usr/lib/python2.7/dist-packages/apt/package.py", line 42, in <module>
    import apt.progress.text
  File "/usr/lib/python2.7/dist-packages/apt/progress/__init__.py", line 32, in <module>
    from apt.progress.old import (CdromProgress, DpkgInstallProgress,
  File "/usr/lib/python2.7/dist-packages/apt/progress/old.py", line 35, in <module>
    from apt.progress import base, text
ValueError: bad marshal data (unknown type code)
```

I've tried reinstalling the various individual parts (including python).  Anyone got any other suggestions as to what to try?

Thanks in advance.

Lee

---

### Post by coffeecat on 2012-05-07
Closed - duplicate here:

[http://ubuntuforums.org/showthread.php?t=1974822](http://ubuntuforums.org/showthread.php?t=1974822)

---

