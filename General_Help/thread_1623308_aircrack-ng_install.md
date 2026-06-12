---
title: "aircrack-ng install"
date: 2010-11-16
forum: General Help
---

### Post by slwx on 2010-11-16
Hi, 
I'm having some trouble to install aircrack-ng, following this instructions: [http://www.aircrack-ng.org/doku.php?id=install_aircrack ]("http://www.aircrack-ng.org/doku.php?id=install_aircrack")

I downloaded, unpacked it, but when I try to compile, i get lots of errors..
mathias@mathias:~$ sudo apt-get install build-essential
...
mathias@mathias:~$ wget [http://download.aircrack-ng.org/aircrack-ng-1.1.tar.gz](http://download.aircrack-ng.org/aircrack-ng-1.1.tar.gz)
...
mathias@mathias:~$ tar -zxvf aircrack-ng-1.1.tar.gz
...
mathias@mathias:~$ cd aircrack-ng-1.1
mathias@mathias:~/aircrack-ng-1.1$ make
make -C src all
make[1]: Entering directory `/home/mathias/aircrack-ng-1.1/src'
make -C osdep
make[2]: Entering directory `/home/mathias/aircrack-ng-1.1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/mathias/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o osdep.o osdep.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o network.o network.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux.o linux.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux_tap.o linux_tap.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o radiotap/radiotap-parser.o radiotap/radiotap-parser.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o common.o common.c
ar cru libosdep.a  osdep.o network.o linux.o linux_tap.o radiotap/radiotap-parser.o common.o
ranlib libosdep.a 
touch .os.Linux
make[3]: Leaving directory `/home/mathias/aircrack-ng-1.1/src/osdep'
make[2]: Leaving directory `/home/mathias/aircrack-ng-1.1/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
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
aircrack-ng.c:3934: error: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/mathias/aircrack-ng-1.1/src'
make: *** [all] Error 2

thanks,
Mathi

---

### Post by barrieluv on 2010-11-16
On the assumption that you're using Ubuntu, open a terminal and
```
sudo apt-get install aircrack-ng
```

---

### Post by spiky001 on 2010-11-16
It is in package manager as well

---

### Post by slwx on 2010-11-16
mathias@mathias:~$ sudo apt-get install aircrack-ng
[sudo] password for mathias: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
**E: Kon pakket aircrack-ng niet vinden**

(couldt find packet aircrack-np, sory its dutch)

i think the file /etc/apt/sources.list might be the cause, I have adjusted it. But i dont know how to reset it. (or what to reset it to). 

i'm sory if its noob question!

Thx, 
mathias

---

### Post by Ancanus on 2010-11-16
It is a universe package, so make sure your sources are set correctly:

System -> Administration -> Software Sources

---

### Post by slwx on 2010-11-17
Thanks!

---

