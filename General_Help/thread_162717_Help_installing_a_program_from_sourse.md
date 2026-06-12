---
title: "Help installing a program from sourse"
date: 2006-04-19
forum: General Help
---

### Post by Tortanick on 2006-04-19
I'm trying to install a program from source, however it has trouble recogniseing the OpenSSL headers during the ./configue stage, here is the relivent lines from the log file

configure:6423: gcc -c -g -O2  -D_GNU_SOURCE=1 -I/usr/local/include conftest.c >&5
conftest.c:85:25: error: openssl/ssl.h: No such file or directory
configure:6429: $? = 1
configure: failed program was:
| /* confdefs.h.  */


any idea what I need to do?

---

### Post by croak77 on 2006-04-19
Do you have libssl-dev installed?

---

### Post by Tortanick on 2006-04-19
I now have libssl-dev and no problem thanks.

---

