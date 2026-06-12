---
title: "cross compilation"
date: 2010-02-13
forum: General Help
---

### Post by shariefbe on 2010-02-13
I am trying to croos compile font-config-2.8.0. When compileing i got this error
```

  CC     fc-case.o
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
cc1: error: unrecognized command line option "-mfloat-abi=softfp"
cc1: error: unrecognized command line option "-mfpu=neon"
cc1: error: unrecognized command line option "-mfloat-abi=softfp"
cc1: error: unrecognized command line option "-mfpu=neon"
fc-case.c:1: error: bad value (armv7-a) for -march= switch
fc-case.c:1: error: bad value (cortex-a8) for -mtune= switch
make[3]: *** [fc-case.o] Error 1
make[3]: Leaving directory `/mnt/omap/sources/fontconfig-2.8.0/fc-case'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/mnt/omap/sources/fontconfig-2.8.0/fc-case'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/mnt/omap/sources/fontconfig-2.8.0'
make: *** [all] Error 2

```
I think it is using gcc instead of ARM toolchain. But in make file all are using ARM only. But how only this part can use GCC. I am not sure. if anybody knows the answer will be appretiated.

---

### Post by rocket16 on 2010-02-13
Was the "sudo" statement issued in your compilation command?

---

### Post by shariefbe on 2010-02-13
No i didnt use any sudo command

---

