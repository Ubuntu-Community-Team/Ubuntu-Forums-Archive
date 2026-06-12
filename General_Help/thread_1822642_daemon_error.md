---
title: "daemon error"
date: 2011-08-10
forum: General Help
---

### Post by jibawakee on 2011-08-10
whenever i try to download an app from the software center it says an uhandleble error. how can i fix this 


thankss

---

### Post by dFlyer on 2011-08-10
from the command line run the following command to download your application and than post your errors. We need the full error message.

sudo apt-get install "nameofprogram" 

Put in the name of the program your trying to install and don't use any quotes.

---

### Post by jibawakee on 2011-08-10
here are the details Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

---

