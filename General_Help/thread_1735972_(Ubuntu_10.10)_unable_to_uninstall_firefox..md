---
title: "(Ubuntu 10.10) unable to uninstall firefox."
date: 2011-04-22
forum: General Help
---

### Post by ookiruxoo on 2011-04-22
Sorry if this is in the wrong area. I'm trying to uninstall firefox and its plugins but I receive this error. I do not know how to fix it, any help would be appreciated.

```

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

```

---

### Post by An Sanct on 2011-04-22
Firefox is in the software center, did you try to uninstall it from there or through command line?

---

### Post by ookiruxoo on 2011-04-22
I tried to uninstall through the Ubuntu Software Center.

---

### Post by dino99 on 2011-04-22
i'm not sure you can completly remove it as there are lot of cross dependencies with other apps/packages

but try with synaptic:
- remove/purge (right click) ubuntu-desktop
- remove/purge firefox (and the associated files)

---

