---
title: "libboost1.37-dev"
date: 2009-10-30
forum: General Help
---

### Post by Soki123 on 2009-10-30
Hi, I'm new at this forum, the problem is that when upgrading to Ubuntu 9.10, do not install this libboost1.37-dev if someone can help me please 


```
~# apt-get install libboost1.37-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libboost1.37-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libboost1.37-dev has no installation candidate
```Thanks in Advance and srry my bad english.

---

### Post by Soki123 on 2009-10-30
anyone can help me? i really need that libboost1.37-dev for ubuntu 9.10 =/

---

### Post by happyhamster on 2009-10-30
Try installing: 

libboost-mpi1.37-dev

> 
 boost1.37 (1.37.0-4) unstable; urgency=low
 .
   * patches/function-template.patch: New.  Fix misplaced #ifdef (thanks to
     Caolan McNamara for the patch at
     [https://bugzilla.redhat.com/show_bug.cgi?id=477131](https://bugzilla.redhat.com/show_bug.cgi?id=477131)).  Closes: #511073.
 .
   * control:
   * rules: New packages libboost-mpi1.37.0 and libboost-mpi1.37-dev.
     Closes: #494832, #490242.  Thanks to Tilman Koschnick and Rutger ter
     Borg for their patches.  New -dev package conflicts and replaces
     libboost1.37-dev, since the headers were moved from the latter to the
     former.

[https://lists.ubuntu.com/archives/karmic-changes/2009-May/000333.html](https://lists.ubuntu.com/archives/karmic-changes/2009-May/000333.html)

---

### Post by Soki123 on 2009-10-30
where can download that library? thanks.

---

### Post by happyhamster on 2009-10-30
In a terminal (Applications-->Accessories-->Terminal), type:

sudo apt-get install libboost-mpi1.37-dev

If that doesn't work, could you perhaps show the output of:

uname -a

(It will show exactly which ubuntu version you are using.)

---

### Post by Soki123 on 2009-10-30
Ok it won't work

```
# sudo apt-get install libboost-mpi1.37-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libboost-mpi1.37-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libboost-mpi1.37-dev has no installation candidate
``````
$ uname -a
Linux USER 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
```

---

### Post by Soki123 on 2009-10-31
it install fine on ubuntu 9.04 -.-

---

### Post by morphodone on 2009-10-31
try installing libboost1.38-dev

doesn't look like 1.37 is there anymore

```
apt-cache search libboost
```

---

### Post by Soki123 on 2009-10-31
I have a game server that require Libboost 1.37-dev To run
```

: error while loading shared libraries: libboost_filesystem-mt.so.1.37.0: cannot open shared object file: No such file or directory
```

---

### Post by morphodone on 2009-10-31
Not sure what you could do other than reinstall 9.04

---

### Post by Soki123 on 2009-10-31
> **morphodone said:**
> Not sure what you could do other than reinstall 9.04
Hey thanks you I solved it,Im re-compiling that again and that work thanks :)

---

