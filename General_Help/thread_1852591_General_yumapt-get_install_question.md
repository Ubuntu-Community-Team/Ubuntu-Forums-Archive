---
title: "General yum/apt-get install question"
date: 2011-09-30
forum: General Help
---

### Post by awelton1 on 2011-09-30
I am curious about when updating a package (e.g. GCC4.2 -> GCC4.3) using yum install or apt-get install does the legacy version of the updated package get kept, or is it deleted after the update? 

If it does delete the legacy stuff it wouldnt be that hard to go get it, just wondering if anyone has some insight.

thanks

---

### Post by 3Miro on 2011-09-30
Depends. If you upgrade Firefox or Chrome, then you get only the latest version. GCC is a compiler and sometimes old software cannot be compiled with newer compilers, so people need specific versions of GCC.

Ubuntu has several versions of gcc in the repos and you can install several of them simultaneously. Try typing gcc- and then hit tab twice, you should see a list of possible gcc versions like gcc-4.5 or gcc-4.2. You can also try:
```
ls -al /usr/bin/ | grep gcc
```
which will give you a longer list.

You can also use Synaptic Package Manager to install other gcc versions.

---

### Post by awelton1 on 2011-09-30
question answered. Thanks!

---

