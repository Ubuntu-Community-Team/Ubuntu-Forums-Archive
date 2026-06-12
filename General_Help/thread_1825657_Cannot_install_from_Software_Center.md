---
title: "Cannot install from Software Center"
date: 2011-08-15
forum: General Help
---

### Post by joules78006 on 2011-08-15
Hi,

I'm having problems when i go to download programs from the Software Center.  I get an error that states...

An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the kdebase-runtime-data package. This might mean you need to manually fix this package.

I've tried to research a few different posts about the same problem however, my problem still persists.

When I enter the code "sudo apt-get upgrade", I get the following message

      "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

and when i enter in the code "sudo dpkg --configure," I have no idea what to do next...



Thanks for any of the advice!!! 

-Julian

---

