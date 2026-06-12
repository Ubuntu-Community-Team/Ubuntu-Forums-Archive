---
title: "GNU C Library how do I compile and install?"
date: 2009-11-01
forum: General Help
---

### Post by Vigh on 2009-11-01
GNU C Library how do I compile and install? I need to install v2.8 so that I can get wineasio to work. What i am trying to do is run regsvr32 wineasio.dll in terminal but it is reporting that glibc_2.8 is missing.

---

### Post by iMisspell on 2009-11-01
Does this help you any ?

Check and see if you have source installed, and version.
```
apt-cache policy glibc-source
```
See what available
```
aptitude search glibc
```
or
```
apt-cache policy glibc-###
```

_

---

### Post by Vigh on 2009-11-01
I Installed glibc 2.7 through the synaptic but I need at least version 2.8

---

