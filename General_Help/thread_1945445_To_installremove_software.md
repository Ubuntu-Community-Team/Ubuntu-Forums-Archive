---
title: "To install/remove software"
date: 2012-03-23
forum: General Help
---

### Post by thanigaivelan19 on 2012-03-23
Hi 
I am getting error in Ubuntu Software Center like this. Please Help me

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.



Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


Thanks

Thanigaivelan

---

### Post by linoseros on 2012-03-23
did you try to use the terminal with sudo apt-get update && sudo apt-get dist-upgrade ? may be that'll fix your problem

---

