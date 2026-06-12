---
title: "NORM and Protokit"
date: 2012-08-07
forum: General Help
---

### Post by demonskier on 2012-08-07
Hey folks, 

I'm trying to build the NORM library from :[http://cs.itd.nrl.navy.mil/work/norm/index.php](http://cs.itd.nrl.navy.mil/work/norm/index.php)

(it uses protokit as a dependency that it includes which must also be built)

I first go build the protokit libraries then try and build the NORM library but when I do it just spits back that libProtokit.a is up to date and never builds the NORM library.

If you've got any insight that would be great.

---

### Post by steeldriver on 2012-08-07
perhaps it is just defaulting to remaking the lib because it is the default target in the makefile - have you tried naming the target explicitly i.e.

```
make -f Makefile.linux norm
```

---

### Post by demonskier on 2012-08-07
Thanks, that worked!

---

### Post by steeldriver on 2012-08-07
always helps to read the instructions ;) 

when you get a moment please mark the thread as solved

---

