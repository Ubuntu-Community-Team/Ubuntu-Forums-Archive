---
title: "Can't install applications"
date: 2010-11-15
forum: General Help
---

### Post by snk429 on 2010-11-15
I just installed Ubuntu. I like it so far.

After installing like 10 apps, I started getting this error :

> An unhandlable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [www..](www..)...................



DETAILS:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 938, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the libreadline5 package. This might mean you need to manually fix this package.









So how do I fix this problem?

---

### Post by zornp on 2010-11-15
got the exact same error.
except of the last row which in my case says:

> SystemError: E:I wasn't able to locate file for the gnuplot-nox package. This might mean you need to manually fix this package.

---

### Post by 311005901 on 2010-11-15
Are you using the Ubuntu Software Center or Synaptic?

---

### Post by zornp on 2010-11-15
the software center

---

### Post by zornp on 2010-11-15
after applying the changes in synaptic the 2nd time - i got the program working..

and after that the software center works again too (:

---

