---
title: "Problem with generation of shared library in Ubuntu 11.10"
date: 2011-10-19
forum: General Help
---

### Post by sidebaet on 2011-10-19
Hi, I work on a project that uses shared library  to do a bridge between java code and C code. The .so library are  corectly generated but when I want to link them I have a problem. In  fact come from the upgrade of my system since Ubuntu 11.04 to Ubuntu  11.10. The followng script works on Ubuntu 11.04 and not on Ubuntu 11.10  and I have no idea of why .
 gcc -shared -o libmonster.so \
 -Wl,-sonam,libmonster.so \
 -Wl,--whole-archive libnusmv.so \
 -Wl,--whole-archive libnugat.so \
 -Wl,--no-whole-archive
 Can you help me?
 Best,
Simon

---

