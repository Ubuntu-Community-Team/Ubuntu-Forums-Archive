---
title: "apt-get error"
date: 2011-02-14
forum: General Help
---

### Post by rockstarrem on 2011-02-14
Hey guys,

The installation seemed stuck so I closed the shell and am getting this error now...

```

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the libmono-data-tds2.0-cil package. This might mean you need to manually fix this package.

```

The installation was definitely stuck, I had this EXACT same problem before with Chrome. Not sure how to resolve this, any help? Please?? :) 

**Need MAJOR help, CANNOT install ANYTHING through Synaptic or anything!**

---

### Post by Habitual on 2011-02-14
try this in terminal:
```
sudo dpkg --configure -a
```

then try to update the package you wanted.

NOTE: FWIW: Don't EVER close a working update/upgrade. It is nearly always a disaster.
Just let 'er run....

---

### Post by rockstarrem on 2011-02-14
That works if I remove the lock on dpkg, and then after that I need to reconfigure it, and then after that I need to remove the lock on apt's archives, then after that I need to run everything with --fix-missing and it still freezes...

I know it usually ends in a disaster, but at the time that I exited it when I needed to update Chrome, I had no choice really, I was leaving class in connecting through SSH.

---

