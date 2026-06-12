---
title: "mingw32 compiling with openssl"
date: 2010-05-01
forum: General Help
---

### Post by littlebuntu on 2010-05-01
hi,  
  I am trying to compile a C code for windows on ubuntu with "i586-mingw32msvc-gcc" But it gives an error message as follows

       $ i586-mingw32msvc-gcc -o my_prog.exe rout1.c  rout2.c -static -lcrypto
       rout2.c:21:25: error: openssl/md5.h: No such file or directory
       rout2.c:22:25: error: openssl/des.h: No such file or directory

where the code file rout2.c is as follows
 
        #include <openssl/md5.h>
        #include <openssl/des.h>

The libssl-dev package (openssl) is installed as the same code compiles correctly with "gcc" for linux  platform. So the only problem is that it doesnt compile with mingw32 despite the header files are present.
Can some please help ??

---

