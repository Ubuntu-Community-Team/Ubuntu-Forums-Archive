---
title: "HELP. when installing/removing apps i get &quot;An unhandlable error occured&quot; +more errors"
date: 2011-07-29
forum: General Help
---

### Post by oadam11 on 2011-07-29
When removing an app I get this error:

An unhandlable error occured:
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


When trying to install new apps I get the Unable to lock the administration directory (/var/lib/dpkg/)
and
Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)

I am on ubuntu 11.04 using gnome 3. I have had no problems up until today, after I installed wine. But now I cant even remove wine thanks to this error. 

Do you have any suggestions on what to do. I have restarted my computer so I don't know how any package managers could be open.


Because of this error, I cannot install or remove any apps. I cant even upgrade. Please help

---

### Post by oadam11 on 2011-07-29
any suggestions?

---

