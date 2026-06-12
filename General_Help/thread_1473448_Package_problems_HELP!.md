---
title: "Package problems HELP!"
date: 2010-05-05
forum: General Help
---

### Post by ubudog on 2010-05-05
Hi guys, just installed Ubuntu 10.04 and installed the flightgear package and the fgfs-base package.  I ran fgfs from a terminal and got this error:
```
$ fgfs
fgfs: error while loading shared libraries: libOpenThreads.so.12: cannot open shared object file: No such file or directory

```$
So then I did: 
```
sudo apt-get install libopenthreads12
```
and it gave me these errors:
```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flightgear: Depends: libalut0 (>= 1.1.0-1) but it is not going to be installed
  simgear1.9.1: Depends: libalut0 (>= 1.1.0-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

And I did try sudo apt-get -f install with no success.  Any help? Thanks. :p

---

### Post by ubudog on 2010-05-05
Fixed it with aptitude.

---

