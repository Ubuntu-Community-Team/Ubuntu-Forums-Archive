---
title: "boost package missing"
date: 2010-02-15
forum: General Help
---

### Post by shariefbe on 2010-02-15
I am trying to cross compile the "libtorrent-rasterbar-0.14.8"
 i got the error 
```

checking for boostlib >= 1.35... yes
checking whether the Boost::System library is available... yes
checking for exit in -lboost_system-mt... no
checking for exit in -lboost_system-mt... (cached) no
checking for exit in -lboost_system-mt... (cached) no
configure: error: Could not link against boost_system-mt !
Configuration of glib library  has failed
sharief@sharief-desktop:/mnt/omap/sources/libtorrent-rasterbar-0.14.8$ 

```
I didnt understand what will be the error. can anyone tell me if you know

---

### Post by shariefbe on 2010-02-16
yes i saw in the config.log file.see that config.log
```

configure:15140: checking for boostlib >= 1.35
configure:15194: arm-none-linux-gnueabi-g++ -c -O3 -march=armv7-a -mtune=cortex-a8 -mcpu=cortex-a8 -mfloat-abi=softfp -mfpu=neon -ftree-vectorize -funroll-all-loops -O3 -march=armv7-a -mtune=cortex-a8 -mcpu=cortex-a8 -mfloat-abi=softfp -mfpu=neon -ftree-vectorize -funroll-all-loops -I/usr/include conftest.cpp >&5
cc1plus: warning: include location "/usr/include" is unsafe for cross-compilation
configure:15194: $? = 0
configure:15196: result: yes
configure:15894: checking whether the Boost::System library is available
configure:15918: arm-none-linux-gnueabi-g++ -c -O3 -march=armv7-a -mtune=cortex-a8 -mcpu=cortex-a8 -mfloat-abi=softfp -mfpu=neon -ftree-vectorize -funroll-all-loops -O3 -march=armv7-a -mtune=cortex-a8 -mcpu=cortex-a8 -mfloat-abi=softfp -mfpu=neon -ftree-vectorize -funroll-all-loops -I/usr/include conftest.cpp >&5
cc1plus: warning: include location "/usr/include" is unsafe for cross-compilation
configure:15918: $? = 0
configure:15933: result: yes
configure:15948: checking for exit in -lboost_system-mt
configure:15973: arm-none-linux-gnueabi-gcc -o conftest -O3 -march=armv7-a -mtune=cortex-a8 -mcpu=cortex-a8 -mfloat-abi=softfp -mfpu=neon -ftree-vectorize -funroll-all-loops -O3 -march=armv7-a -mtune=cortex-a8 -mcpu=cortex-a8 -mfloat-abi=softfp -mfpu=neon -ftree-vectorize -funroll-all-loops -I/usr/include  -L/usr/lib conftest.c -lboost_system-mt   >&5
cc1: warning: include location "/usr/include" is unsafe for cross-compilation
conftest.c:33: warning: conflicting types for built-in function 'exit'
/mnt/freescale/toolchain/bin/../lib/gcc/arm-none-linux-gnueabi/4.4.1/../../../../arm-none-linux-gnueabi/bin/ld: warning: library search path "/usr/lib" is unsafe for cross-compilation
/mnt/freescale/toolchain/bin/../lib/gcc/arm-none-linux-gnueabi/4.4.1/../../../../arm-none-linux-gnueabi/bin/ld: skipping incompatible /usr/lib/libboost_system-mt.so when searching for -lboost_system-mt
/mnt/freescale/toolchain/bin/../lib/gcc/arm-none-linux-gnueabi/4.4.1/../../../../arm-none-linux-gnueabi/bin/ld: skipping incompatible /usr/lib/libboost_system-mt.a when searching for -lboost_system-mt
/mnt/freescale/toolchain/bin/../lib/gcc/arm-none-linux-gnueabi/4.4.1/../../../../arm-none-linux-gnueabi/bin/ld: cannot find -lboost_system-mt
collect2: ld returned 1 exit status

```

it is searching the path of host system libraries. that is in /usr/lib but in configure it is denoted the path where i installed cross compiled libraries. but it didnt taled that. it is taking my host system libraries. why? see my configuration file

[http://www.easy-share.com/1909302568/configure.txt](http://www.easy-share.com/1909302568/configure.txt)

---

