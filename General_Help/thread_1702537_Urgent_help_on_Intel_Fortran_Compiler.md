---
title: "Urgent help on Intel Fortran Compiler"
date: 2011-03-07
forum: General Help
---

### Post by fallschirmjaeger on 2011-03-07
I am new to linux and installed intel fortran compiler as per the instructions and also set the environment variables in . bashrc 

when i complie the fortran file it gives this error... i have installed all necessary libraries...could someone kindly help me ? ... thanking you in advance..

ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../..//libm.so when searching for -lm
ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../..//libm.a when searching for -lm
ld: skipping incompatible /usr/lib//libm.so when searching for -lm
ld: skipping incompatible /usr/lib//libm.a when searching for -lm
ld: skipping incompatible //usr/lib/libm.so when searching for -lm
ld: skipping incompatible //usr/lib/libm.a when searching for -lm
ld: cannot find -lm
ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../..//libc.so when searching for -lc
ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../..//libc.a when searching for -lc
ld: skipping incompatible /usr/lib//libc.so when searching for -lc
ld: skipping incompatible /usr/lib//libc.a when searching for -lc
ld: skipping incompatible //usr/lib/libc.so when searching for -lc
ld: skipping incompatible //usr/lib/libc.a when searching for -lc
ld: cannot find -lc
ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5//libgcc_s.so when searching for -lgcc_s
ld: cannot find -lgcc_s
ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5//libgcc.a when searching for -lgcc
ld: cannot find -lgcc
ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../..//libdl.so when searching for -ldl
ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../..//libdl.a when searching for -ldl
ld: skipping incompatible /usr/lib//libdl.so when searching for -ldl
ld: skipping incompatible /usr/lib//libdl.a when searching for -ldl
ld: skipping incompatible //usr/lib/libdl.so when searching for -ldl
ld: skipping incompatible //usr/lib/libdl.a when searching for -ldl
ld: cannot find -ldl
ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../..//libc.so when searching for -lc
ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../..//libc.a when searching for -lc
ld: skipping incompatible /usr/lib//libc.so when searching for -lc
ld: skipping incompatible /usr/lib//libc.a when searching for -lc
ld: skipping incompatible //usr/lib/libc.so when searching for -lc
ld: skipping incompatible //usr/lib/libc.a when searching for -lc
ld: cannot find -lc

---

### Post by fallschirmjaeger on 2011-03-08
Alrite I fixed it myself. The problem seems to be downloading the combined package of intel fortran 32/i86-64 bit. I uninstalled and downloaded only ia32 for 32 bit system and it followed general instructions given on intel forums and it works fine. If you are on 64 bit machine then download the individual package. if you are smart enough, download combined package but work out the path to lib files so that the ifort takes right directory.

---

