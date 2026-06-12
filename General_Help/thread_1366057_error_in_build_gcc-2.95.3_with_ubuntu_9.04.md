---
title: "error in build gcc-2.95.3 with ubuntu 9.04"
date: 2009-12-28
forum: General Help
---

### Post by e2rwin on 2009-12-28
i'm still build an embedded linux system on embedded pc csb625 (arm architecture) with ubuntu 9.04 as host pc. now i still build gnu arm toolchain, but i have problems in my project. 
i'm using binutils 2.16.1, gcc-2.95.3, glibc 2.2.2 and linux kernel 2.6.11.3. 

binutils configuration succed, but i have problem at build bootsrap gcc compiler. problem in my terminal like this :

    inlined from ‘collect_execute’ at /home/erwin/ikhwan-project-2/build-tools/gcc-2.95.3/gcc/collect2.c:1762:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[1]: *** [collect2.o] Error 1
make[1]: Leaving directory `/home/erwin/ikhwan-project-2/build-tools/gcc'
make: *** [all-gcc] Error 2

at make all-gcc.

i need help for my problems, thanks a lot for all.

---

### Post by dcstar on 2009-12-28
> **e2rwin said:**
> i'm still build an embedded linux system on embedded pc csb625 (arm architecture) with ubuntu 9.04 as host pc. now i still build gnu arm toolchain, but i have problems in my project. 
i'm using binutils 2.16.1, gcc-2.95.3, glibc 2.2.2 and linux kernel 2.6.11.3. 

binutils configuration succed, but i have problem at build bootsrap gcc compiler. problem in my terminal like this :

    inlined from &#8216;collect_execute&#8217; at /home/erwin/ikhwan-project-2/build-tools/gcc-2.95.3/gcc/collect2.c:1762:
/usr/include/bits/fcntl2.h:51: error: call to &#8216;__open_missing_mode&#8217; declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[1]: *** [collect2.o] Error 1
make[1]: Leaving directory `/home/erwin/ikhwan-project-2/build-tools/gcc'
make: *** [all-gcc] Error 2

at make all-gcc.

i need help for my problems, thanks a lot for all.

People do not compile things generally, ask programing questions in the Programing forum.

---

