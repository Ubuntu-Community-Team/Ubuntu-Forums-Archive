---
title: "firefox and chrome crash"
date: 2011-09-25
forum: General Help
---

### Post by erelsgl on 2011-09-25
After the most recent update, both Firefox and Chrome crash with the following error message:
 
Inconsistency detected by ld.so: dl-open.c: 582: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!
 
I tried to reinstall them, didn't help.
 
I am on Wubi, Ubuntu 10.04.
 
Any hint?

---

### Post by erelsgl on 2011-09-25
Solved by removing googletalk-plugin and some other google-related packages.

---

