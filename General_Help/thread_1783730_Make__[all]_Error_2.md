---
title: "Make: *** [all] Error 2"
date: 2011-06-16
forum: General Help
---

### Post by Abdul.I on 2011-06-16
Hi,

When I try to compile software the initial ./configure command works as it should but when I try the make command I get the following error:

D_FORTIFY_SOURCE=2  -O2 -Wall -Wextra  -fno-strict-aliasing  crypto.cc -o crypto.o
crypto.cc: In function ‘void deskey(unsigned char*, int)’:
crypto.cc:545: error: ‘DE1’ was not declared in this scope
crypto.cc: In function ‘void cookey(long unsigned int*)’:
crypto.cc:590: error: ‘usekey’ was not declared in this scope
make[1]: *** [crypto.o] Error 1
make[1]: Leaving directory `/home/abdul/Downloads'
make: *** [all] Error 2

OR when I use the Make Install command I get the the error:

make[3]: *** [install-libnetincludeHEADERS] Error 1
make[3]: Leaving directory `/home/abdul/Downloads/libnet/include/libnet'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/abdul/Downloads/libnet/include/libnet'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/abdul/Downloads/libnet/include'
make: *** [install-recursive] Error 1

Thank you.

---

### Post by dagoss on 2011-06-16
It might help to know what package you are trying to compile? Have you read the INSTALL instructions? Perhaps you missed a dependency?

---

