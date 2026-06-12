---
title: "Error's when trying to compile Aircrack-ng suite"
date: 2009-07-19
forum: General Help
---

### Post by JayUK20 on 2009-07-19
I couldn't find a .deb package for aircrack suite so I am trying to compile it myself and I am having errors when I use the make command.

> wubi@ubuntu:~/Documents/aircrack-ng-1.0-rc3$ make
make -C src all
make[1]: Entering directory `/home/wubi/Documents/aircrack-ng-1.0-rc3/src'
make -C osdep
make[2]: Entering directory `/home/wubi/Documents/aircrack-ng-1.0-rc3/src/osdep'
Building for Linux
make[3]: Entering directory `/home/wubi/Documents/aircrack-ng-1.0-rc3/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/wubi/Documents/aircrack-ng-1.0-rc3/src/osdep'
make[2]: Leaving directory `/home/wubi/Documents/aircrack-ng-1.0-rc3/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
In file included from aircrack-ng.c:69:
sha1-sse2.h: In function ‘calc_4pmk’:
sha1-sse2.h:143: error: implicit declaration of function ‘HMAC’
sha1-sse2.h:143: error: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c: In function ‘crack_wpa_thread’:
aircrack-ng.c:3876: error: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/wubi/Documents/aircrack-ng-1.0-rc3/src'
make: *** [all] Error 2
wubi@ubuntu:~/Documents/aircrack-ng-1.0-rc3$

---

### Post by michy99 on 2009-07-19
aircrack-ng is available in the repositories. Make sure you have the universe repository enabled.

---

### Post by JayUK20 on 2009-07-19
Thanks but it didn't install all the extras for some reason, however I have finally compiled it and have everything I need.

---

### Post by morpheus063 on 2009-09-28
> **JayUK20 said:**
> Thanks but it didn't install all the extras for some reason, however I have finally compiled it and have everything I need.

Hey JayUK20, I am also facing the same issue. Do you mind sharing what you did to resolve the issue?

---

### Post by GreekRockNRoller on 2011-01-15
hey dudes before you try to compile you need the following libraries installed: libssl-dev 
build-essential lbsqlite3-dev

---

