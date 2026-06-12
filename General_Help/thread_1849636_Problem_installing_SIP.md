---
title: "Problem installing SIP"
date: 2011-09-24
forum: General Help
---

### Post by Ty Kez on 2011-09-24
Need help installing SIP i am getting the following errors when i  "make"  :

tyler@ubuntu:~/sip41$ sudo make
make[1]: Entering directory `/home/tyler/sip41/sipgen'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/tyler/sip41/sipgen'
make[1]: Entering directory `/home/tyler/sip41/siplib'
gcc -c -pipe -fPIC -O2 -w -DNDEBUG -I. -I/usr/include/python3.2mu -o siplib.o siplib.c
siplib.c:20:20: fatal error: Python.h: No such file or directory
compilation terminated.
make[1]: *** [siplib.o] Error 1
make[1]: Leaving directory `/home/tyler/sip41/siplib'
make: *** [all] Error 2

---

### Post by sffvba[e0rt on 2011-09-24
*Thread moved to **General Help**.*


404

---

### Post by dkolaczynski on 2011-09-29
If you haven't done it yet: _package **python-dev** is required_.

---

