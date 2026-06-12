---
title: "deathaddercfg-004"
date: 2009-11-23
forum: General Help
---

### Post by Raiju on 2009-11-23
I Am trying to install this for my deathadder mouse.

one of the dependencies "libconfig0-dev" isn't in synaptics

When i use 'make' or 'make install' terminal gives out this error
```
cc -std=c99 -O2 -fomit-frame-pointer -Wall -D_BSD_SOURCE -D_GNU_SOURCE -DVERSION_=004   -c -o conffile.o conffile.c
conffile.c:49:26: error: config/parse.h: No such file or directory
conffile.c:65: error: expected ‘)’ before ‘*’ token
conffile.c:78: error: expected ‘)’ before ‘*’ token
conffile.c:88: error: expected ‘)’ before ‘*’ token
conffile.c:152: error: expected ‘)’ before ‘*’ token
conffile.c:174: error: expected ‘)’ before ‘*’ token
conffile.c:250: error: expected ‘)’ before ‘*’ token
conffile.c:310: error: expected ‘)’ before ‘*’ token
conffile.c: In function ‘dadd_read_conffile’:
conffile.c:334: error: ‘section_t’ undeclared (first use in this function)
conffile.c:334: error: (Each undeclared identifier is reported only once
conffile.c:334: error: for each function it appears in.)
conffile.c:334: error: ‘tree’ undeclared (first use in this function)
conffile.c:336: warning: implicit declaration of function ‘parse’
conffile.c:344: warning: implicit declaration of function ‘parse_global_parms’
conffile.c:347: warning: implicit declaration of function ‘parse_global_sections’
conffile.c:351: warning: implicit declaration of function ‘parse_destroy’
make: *** [conffile.o] Error 1
```

---

### Post by Wolfensteine on 2010-10-03
I am also experiencing the same problem.....



:):):)Thanks in Advance:):):)

---

