---
title: "Bacula Install"
date: 2011-03-19
forum: General Help
---

### Post by OldManRiver on 2011-03-19
All,

I have completed install of Bacula, but getting this error trying to run"
```
bconsole
Connecting to Director localhost:9101
19-Mar 19:29 bconsole JobId 0: Fatal error: bsock.c:129 Unable to connect to Director daemon on localhost:9101. ERR=Connection refused
```
Since noobie to this package, what is this error and how is it corrected?

Thanks!

OMR

---

### Post by OldManRiver on 2011-03-19
All,

Solved this by installing WebAdmin, which showed the errors in mysql, and when corrected bacula runs fine from WebAdmin.

Thanks!

OMR

---

