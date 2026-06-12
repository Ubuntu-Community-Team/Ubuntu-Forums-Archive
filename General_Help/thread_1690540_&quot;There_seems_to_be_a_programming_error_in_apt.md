---
title: "&quot;There seems to be a programming error in aptdaemon&quot;"
date: 2011-02-18
forum: General Help
---

### Post by mikmalot on 2011-02-18
I was installing a program using the Ubuntu Software Center, and the whole system completely locked up, so I was forced to press teh power button to reset it. When I logged back in, I get this error whenever trying to install or remove something:

An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the kdelibs-data package. This might mean you need to manually fix this package.

Help?

---

