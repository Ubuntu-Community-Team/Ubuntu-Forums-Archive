---
title: "Can't Install Software from Software Centre"
date: 2011-12-29
forum: General Help
---

### Post by niknat on 2011-12-29
Hi all,

TOTALLY new to Linux and ubuntu, so if you have a solution, please bear in mind that your explanation will have to suit a total newbie!  :)

Whatever I try to install using the Ubuntu Software Centre, returns this message ...

An Unhandleable Error Occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


Thanks for any help you can give.

Regards,

Nik

---

### Post by Rubi1200 on 2011-12-30
Hi and welcome to the forums :-)

Open a terminal with Ctr+Alt+T and run the following commands (best to copy and paste):

```
sudo apt-get clean  
sudo apt-get update  
sudo apt-get upgrade
```
If there are errors reported, post them here.

---

