---
title: "PHP5  uuid_create yields segfault in libuuid.so"
date: 2009-10-27
forum: General Help
---

### Post by s2theg on 2009-10-27
Calling uuid_create in the PHP uuid package yields the text "Segfault"

The /var/log/syslog lists the following error message

segfault at 44 ip 00007fec10c8184a sp 00007fff24e96400 error 6 in libuuid.so.1.2[7fec10c80000+3000]

I know this is what caused the segfault because uuid uses libuuid.

I'm not sure what else to do. It looks like the library is broken in this release.

I am using Ubuntu 9.04

---

