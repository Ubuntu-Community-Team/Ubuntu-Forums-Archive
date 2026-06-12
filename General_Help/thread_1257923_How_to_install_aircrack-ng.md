---
title: "How to install aircrack-ng"
date: 2009-09-04
forum: General Help
---

### Post by RedWind on 2009-09-04
I am following the readme file and i keep getting errors

```
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
In file included from aircrack-ng.c:69:
sha1-sse2.h: In function ‘calc_4pmk’:
sha1-sse2.h:140: error: implicit declaration of function ‘HMAC’
sha1-sse2.h:140: error: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c: In function ‘crack_wpa_thread’:
aircrack-ng.c:3910: error: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/red/installs/aircrack-ng-1.0-rc4/src'
make: *** [install] Error 2
```

---

### Post by Sub101 on 2009-09-04
Aircrack is in the repos. Its easier to install from there.

---

