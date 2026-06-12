---
title: "Make errors!!"
date: 2009-12-17
forum: General Help
---

### Post by serpantman on 2009-12-17
```

bash-3.1# make
Making all in src
make[1]: Entering directory `/root/Downloads/webcam_server-0.50/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/Downloads/webcam_server-0.50/src'
Making all in man
make[1]: Entering directory `/root/Downloads/webcam_server-0.50/man'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/root/Downloads/webcam_server-0.50/man'
make[1]: Entering directory `/root/Downloads/webcam_server-0.50'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/root/Downloads/webcam_server-0.50'

```

btw.. im root, and i ran configure first, everything went smooth as far as i can tell, what is going on here?

---

### Post by eric3_14159 on 2010-01-15
It doesn't seem to have any work to do. Have you tried "make install" or whatever else is indicated by the documentation (probably README, INSTALL, or docs/something) to begin using the software?

---

