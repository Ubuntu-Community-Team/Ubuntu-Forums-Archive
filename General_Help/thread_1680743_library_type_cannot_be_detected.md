---
title: "library type cannot be detected"
date: 2011-02-03
forum: General Help
---

### Post by draki on 2011-02-03
[I've posted this on the Opera forums as well....]

I'm running Ubuntu 10.10: Linux 2.6.35-25-generic #44-Ubuntu x86_64 GNU/Linux
Opera:Version information
Version 11.01
Build 1190
Platform Linux
System x86_64, 2.6.35-25-generic
Browser identification Opera/9.80 (X11; Linux x86_64; U; en-GB) Presto/2.7.62 Version/11.01

I'm getting weird problems - hanging for a few seconds, hanging for ages and the occasional crash. Seems to sometimes be triggered by the mouse wheel, but also happens when just reading a webpage

When I run opera from the command line I get the following errors:

```
 opera
WARNING: /usr/lib/libc.so: library type cannot be detected
Inconsistency detected by ld.so: dl-close.c: 736: _dl_close: Assertion `map->l_init_called' failed!
WARNING: /usr/lib/libpthread.so: library type cannot be detected
WARNING: /usr/lib/libc.so: library type cannot be detected
Inconsistency detected by ld.so: dl-close.c: 736: _dl_close: Assertion `map->l_init_called' failed!
WARNING: /usr/lib/libpthread.so: library type cannot be detected
WARNING: /usr/lib/libc.so: library type cannot be detected
Inconsistency detected by ld.so: dl-close.c: 736: _dl_close: Assertion `map->l_init_called' failed!
WARNING: /usr/lib/libpthread.so: library type cannot be detected
WARNING: /usr/lib/libc.so: library type cannot be detected
Inconsistency detected by ld.so: dl-close.c: 736: _dl_close: Assertion `map->l_init_called' failed!
WARNING: /usr/lib/libpthread.so: library type cannot be detected 
```

I've spent a while on Google and cannot find any reference to this error - except for a vague reference to flash...

Does anyone have any idea on this? It's very frustrating!

thanks in advance

---

### Post by draki on 2011-02-05
Someone on the Opera forums suggested a conflict between 32bit and 64bit libraries...
[http://my.opera.com/community/forums/topic.dml?id=898772&t=1296762387&page=1#comment8557722]("http://my.opera.com/community/forums/topic.dml?id=898772&t=1296762387&page=1#comment8557722")

Does anyone have any ideas which libraries may be causing this?

---

