---
title: "An unhandled error occured.."
date: 2011-09-26
forum: General Help
---

### Post by zimsabre on 2011-09-26
Hi, im new to Ubuntu, when trying to install a new program i get this error..

> There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.

Details

> Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


Any help would be apresiated.

---

### Post by zimsabre on 2011-09-26
Strangly i love google, fixed..

I was stuck at a licence agrement and did not know how to continue. 
i had to "tab enter"

Many thank's.

---

