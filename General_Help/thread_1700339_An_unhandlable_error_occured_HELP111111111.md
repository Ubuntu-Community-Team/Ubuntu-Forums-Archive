---
title: "An unhandlable error occured HELP111111111"
date: 2011-03-04
forum: General Help
---

### Post by sesipdo on 2011-03-04
i was installing wine for ubuntu and i think my laptop went to sleep in  the process and now when i go to install any other program i get this  message 


----------------------
There seems to be a programming error in aptdaemon, the software that  allows you to install/remove software and to perform other package  management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.
-------- ERRORS -------------------

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the  ttf-mscorefonts-installer package. This might mean you need to manually  fix this package.
------------------------------------------:(:(

---

### Post by Krytarik on 2011-03-05
Try those commands:
```
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
```
If that goes well, update your package information thereafter, and try to upgrade:
```
sudo apt-get update
sudo apt-get upgrade
```

---

