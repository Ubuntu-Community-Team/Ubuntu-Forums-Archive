---
title: "Trying to build an ARM-linux cross compiler off of GCC 2.95.2"
date: 2009-10-27
forum: General Help
---

### Post by Fenix1186 on 2009-10-27
Hello,

I'm a complete beginner to ubuntu and linux in general. I'm trying to make an arm-linux cross compiler for a senior design project. I'm using the simplescalar ANNOUNCE.cross file to go thorough this and have successfully created the binutils. I'm now trying to build the gcc 2.95.2 but I get the following error:

[SIZE=2]...
./config/arm/arm.c: In function ‘arm_override_options’:
./config/arm/arm.c:286: warning: assignment discards qualifiers from pointer target type
./config/arm/arm.c:530: error: lvalue required as left operand of assignment
make[1]: *** [arm.o] Error 1
make[1]: Leaving directory `/home/user1/arm_cross/gcc-2.95.3/gcc'
make: *** [all-gcc] Error 2[/SIZE]


   ./configure --target=arm-linux --prefix=/home/user1/example/arm-cross
   make LANGUAGES=c BOOT_LDFLAGS=-static

Does anyone know what I'm doing wrong??

---

### Post by Fenix1186 on 2009-10-27
Bump, anyone please??

---

### Post by e2rwin on 2009-12-28
in line 530 file arm.c (/gcc/config/arm) with

  arm_prgmode = TARGET_APCS_32 ? PROG_MODE_PROG32 : PROG_MODE_PROG26;

---

