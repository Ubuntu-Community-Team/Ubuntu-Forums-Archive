---
title: "Sudo apt-get error"
date: 2011-01-09
forum: General Help
---

### Post by pankaj.sea on 2011-01-09
Hi!
I'm using 10.10 and from today I'm getting this error > dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. When I'm trying to install any software using ```
sudo apt-get <sw-name>
```Also I'm unable install using "Ubuntu Software Center", showing unhandleable error. Here is the details:
> Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
Please give a solution!
:( :confused:

---

### Post by owners4life5 on 2011-01-09
see post below...

---

### Post by owners4life5 on 2011-01-09
not to state the obvious or anything, but have you tried running ```
sudo dpkg --configure -a
``` yet?

---

### Post by avlnewby on 2011-01-09
Hi; i'm getting same error and have tried suggestion above in terminal. Response from terminal is: status database area is locked by another process

---

### Post by lbarnes on 2011-01-09
> **avlnewby said:**
> Hi; i'm getting same error and have tried suggestion above in terminal. Response from terminal is: status database area is locked by another process
Be sure Synaptic or Update Manager is closed.

---

### Post by avlnewby on 2011-01-09
you da man!

---

### Post by pankaj.sea on 2011-01-09
> sudo dpkg --configure -a has solved the problem!
:)
Thanks...

---

