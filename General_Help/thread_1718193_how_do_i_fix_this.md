---
title: "how do i fix this"
date: 2011-03-30
forum: General Help
---

### Post by kkyod on 2011-03-30
when i try to install any app i get this error

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

---

### Post by wolfen69 on 2011-03-31
I would open synaptic package manager and look for any broken packages and fix them. Let us know what happens.

---

