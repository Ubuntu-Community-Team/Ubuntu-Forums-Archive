---
title: "Can't download Mixxx or GStreamer plugins"
date: 2011-12-04
forum: General Help
---

### Post by iamnigel on 2011-12-04
I tried to download Mixxx and the GStreamer plugins from the Ubuntu Software Center and for some reason, it wouldn't let me download either. I need GStreamer to listen to all of my songs, and Mixxx would just be nice to have. An error message comes up with the heading "An unhandlable error occured." And here are the details under that.

"There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package."

---

### Post by diegojp on 2013-01-18
> **iamnigel said:**
>  SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package."

Try to play installing/removing/purging that package, then try to install Mixxx or whatever

---

