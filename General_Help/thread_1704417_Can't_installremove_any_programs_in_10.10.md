---
title: "Can't install/remove any programs in 10.10"
date: 2011-03-10
forum: General Help
---

### Post by nate433 on 2011-03-10
Hi everyone I'm pretty new to Linux and everything has gone smoothly until recently. Every program i try to install/remove from the software center or terminal gives me this error message:

"**An unhandlable error occured**

Details: Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package."

Thank you in advanced

---

### Post by lithopsian on 2011-03-10
Time to learn the command line. Just to check your system is OK, try:
```

sudo apt-get update
sudo apt-get upgrade

```Now, to fix your aptdaemon problem, you could try to install that font package:
```

sudo apt-get install ttf-mscorefonts-installer

```If it says it is already installed and the latest version, try:
```

sudo apt-get install --reinstall ttf-mscorefonts-installer

```

---

### Post by nate433 on 2011-03-10
Thank you this fixed everything. Now to go look up what actually just happened.

---

