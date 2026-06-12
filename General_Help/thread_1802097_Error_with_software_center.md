---
title: "Error with software center"
date: 2011-07-11
forum: General Help
---

### Post by Rennonz on 2011-07-11
Trying to download cheese from the software center, it crashes and I get this message-

> Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the libmysqlclient16 package. This might mean you need to manually fix this package.

So, as a result I can't download it. I'm using 11.04 standard Ubuntu.

Anyone can help?

---

### Post by CesarOscar on 2011-07-11
Open the terminal and type:
```
sudo apt-get -f install cheese
```

This should download, fix (-f) and install cheese.

---

### Post by Rennonz on 2011-07-11
Thanks CesarOscar, it worked but I'm wondering if it was just the software center  which was faulty or is it something wrong with my ubuntu?

---

