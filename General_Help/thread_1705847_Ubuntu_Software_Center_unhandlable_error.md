---
title: "Ubuntu Software Center unhandlable error"
date: 2011-03-12
forum: General Help
---

### Post by aetherian on 2011-03-12
'ello, just installed ubuntu on my laptop (msi gt640) and, whilst attempting to install something from the software center, get an error. in full, it is:

[CENTER]There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

[LEFT]Under Details, it states:

[CENTER]Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
[LEFT]
Any help would be amazing. thanks in advance.
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]

---

### Post by Krytarik on 2011-03-13
Please run the following command in a terminal, and when you get a confirmation dialog, press TAB to select <Ok>, then press Enter/Return:
```
sudo dpkg --configure -a
```After doing so, hopefully successful, run the following commands to check if everything is fine:
```
sudo apt-get update
sudo apt-get upgrade
```If you get any errors, run those commands and then try again:
```
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install
```

---

