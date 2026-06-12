---
title: "facing problem to build an ARM-linux cross compiler"
date: 2011-04-21
forum: General Help
---

### Post by tonmoyt7 on 2011-04-21
Hello everyone,
 i m trying to make an arm-linux cross compiler for a my project. I'm now trying to build the gcc 2.95.2 but when i use the following command:
**make LANGUAGES=c BOOT_LDFLAGS=-static**
it shows the following error:[I]
[B][SIZE=2]...
./config/arm/arm.c: In function ‘arm_override_options’:
./config/arm/arm.c:286: warning: assignment discards qualifiers from pointer target type
./config/arm/arm.c:530: error: lvalue required as left operand of assignment
make[1]: *** [arm.o] Error 1
make[1]: Leaving directory `/home/user1/arm_cross/gcc-2.95.3/gcc'
make: *** [all-gcc] Error [/SIZE][/B][/I]
Does any one know how to solve this problem.

I am using ubuntu-10.10

---

