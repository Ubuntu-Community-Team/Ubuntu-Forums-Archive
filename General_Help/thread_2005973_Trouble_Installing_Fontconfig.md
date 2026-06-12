---
title: "Trouble Installing Fontconfig"
date: 2012-06-18
forum: General Help
---

### Post by rubxcubedude on 2012-06-18
I am trying to install fontconfig on my machine so that i can install cairo(with the end goal of installing gtk).

I run ./configure on fontconfig and everything works fine. However, when i run the make install command i get an error message saying 
```

/compilers/arm-gcc-3.3.4-glibc-2.3.2/lib/gcc-lib/arm-linux/3.3.4/../../../../arm-linux/bin/ld: ERROR: /targets/ts73x0/lib/libxml2.so is compiled for EABI version 0, whereas .libs/libfontconfig.so.1.4.4 is compiled for version 5
File format not recognized: failed to merge target specific data of file /targets/ts73x0/lib/libxml2.so
/compilers/arm-gcc-3.3.4-glibc-2.3.2/lib/gcc-lib/arm-linux/3.3.4/../../../../arm-linux/bin/ld: ERROR: //compilers/arm-gcc-3.3.4-glibc-2.3.2/lib/gcc-lib/arm-linux/3.3.4/../../../../arm-linux/lib/libdl.so is compiled for EABI version 0, whereas .libs/libfontconfig.so.1.4.4 is compiled for version 5
File format not recognized: failed to merge target specific data of file /compilers/arm-gcc-3.3.4-glibc-2.3.2/lib/gcc-lib/arm-linux/3.3.4/../../../../arm-linux/lib/libdl.so
/scratchbox/compilers/arm-gcc-3.3.4-glibc-2.3.2/lib/gcc-lib/arm-linux/3.3.4/../../../../arm-linux/bin/ld: ERROR: /targets/ts73x0/lib/libz.so is compiled for EABI version 0, whereas .libs/libfontconfig.so.1.4.4 is compiled for version 5
File format not recognized: failed to merge target specific data of file /targets/ts73x0/lib/libz.so
/compilers/arm-gcc-3.3.4-glibc-2.3.2/lib/gcc-lib/arm-linux/3.3.4/../../../../arm-linux/bin/ld: ERROR: /compilers/arm-gcc-3.3.4-glibc-2.3.2/lib/gcc-lib/arm-linux/3.3.4/../../../../arm-linux/lib/libm.so is compiled for EABI version 0, whereas .libs/libfontconfig.so.1.4.4 is compiled for version 5

....

```I've compile all packages with the same compiler so I'm not sure why libfontconfig thinks its compiled for version 5. How can i change this so fontconfig compiles correctly?

---

### Post by rubxcubedude on 2012-06-19
bump

---

