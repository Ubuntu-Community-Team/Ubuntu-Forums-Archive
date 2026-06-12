---
title: "How to determine kernel 32-bit or 64-bit"
date: 2010-09-17
forum: General Help
---

### Post by legendbb on 2010-09-17
Google answers attempted:
# grep lm /proc/cpuinfo
# uname -m
# file /sbin/init
# file /usr/bin/file
 
I don't think none of the above give deterministic answer.
 
Since I have 32-bit & 64-bit different system all of above spit out the same info.
 
Shouldn't there be a simple method to tell?
 
Thanks,:KS

---

### Post by endotherm on 2010-09-17
what do you get from 'uname -a'?
mine a 32 bit shows this:
```
Lucid:~$ uname -a
Linux Lucid 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 **i686** GNU/Linux

```I believe that the piece in bold indicates that I am using a 32 bit system. I believe that it will read "AMD64" or some such on a 64bit system.

Edit: ahh as cj mentions the string for 64bit. see below

---

### Post by cj.surrusco on 2010-09-17
You should be able to use 
```
uname -m
```
If it says x86_64, then you know you are on a 64-bit system.

---

