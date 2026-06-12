---
title: "Software Center and CompizConfig Settings Manager not opening"
date: 2011-05-26
forum: General Help
---

### Post by evanct on 2011-05-26
Trying to start software center:

```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 111, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 47, in <module>
    from softwarecenter.backend.aptd import TransactionFinishedResult
  File "/usr/share/software-center/softwarecenter/backend/__init__.py", line 19, in <module>
    from aptd import AptdaemonBackend
  File "/usr/share/software-center/softwarecenter/backend/aptd.py", line 30, in <module>
    from aptdaemon import client
ImportError: No module named aptdaemon

```

I do have aptdaemon and python-aptdaemon installed.

Trying to start CCSM just gives me:

```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 93, in <module>
    import ccm
ImportError: No module named ccm

```

Also, in 11.04 there's a "feature" where if I drag the title bar of a window against the top of the screen, it expands sideways. How do I disable that? I'm guessing I do it in CCSM. Who thought that was a good idea anyway?

---

### Post by evanct on 2011-05-26
bump

---

### Post by WegDamit on 2011-06-19
Try to run this as normal user, that is the one running the gnome session, 
e,g, root won't work,,,

---

