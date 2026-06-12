---
title: "Ubuntu software center gives error (atpdeamon)"
date: 2011-07-20
forum: General Help
---

### Post by hacker_at_linux on 2011-07-20
My software center worked well till yesterday. I installed lamp server. But since them its going all crazy I am not able to install any package. Not even via terminal or synaptic. It gives the following error
An unhandlable error occurred
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

and when I click details it shows the following thing.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the linux-image-2.6.38-10-generic package. This might mean you need to manually fix this package.


I am new to this and don't understand this error at all. Can any one plz help me figure out what would I need to do to fix this error. I am also not able to update my system

Thanx in advance

---

### Post by hacker_at_linux on 2011-07-20
Any one out there plzzz help me I really want to install a couple of packages

---

### Post by jerrrys on 2011-07-21
open a terminal and enter:

sudo apt-get update && sudo apt-get upgrade

that should upgrade your kernel.  if not, please post back any errors.

---

### Post by hacker_at_linux on 2011-07-21
it does not. I am posting the error here
```
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 7174 package 'python-egenix-mxdatetime':
 missing description
dpkg: error: parsing file '/var/lib/dpkg/available' near line 7175:
 field name `Package(' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by jerrrys on 2011-07-21
dpkg: error: parsing file '/var/lib/dpkg/available' near line 7175:
 field name `Package(' must be followed by colon

lets take care of this typo

open a terminal and enter: 

sudo gedit /var/lib/dpkg/available

to get line numbers go to:

edit>preferences and check line numbers

and try it again

---

