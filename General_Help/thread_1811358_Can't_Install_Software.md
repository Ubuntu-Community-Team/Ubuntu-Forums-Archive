---
title: "Can't Install Software?"
date: 2011-07-24
forum: General Help
---

### Post by El3mentGamer on 2011-07-24
Everytime i try to install a program off the ubuntu software center i get this error.
Traceback (most recent call last):
  > File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.

---

### Post by IWantFroyo on 2011-07-24
Can you run:

```
sudo apt-get install sun-java6-jre
```?

---

### Post by El3mentGamer on 2011-07-24
this is what i got. > brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo apt-get install sun-java6-jre
[sudo] password for brandon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.26-1natty1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.26-1natty1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

