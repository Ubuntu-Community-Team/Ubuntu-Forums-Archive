---
title: "Need help patching my intel 3945 driver"
date: 2011-06-11
forum: General Help
---

### Post by johnsr11 on 2011-06-11
I am running ubuntu 11.04 and I am trying to patch my drivers. I have the intel 3945. I am following the steps from [http://www.aircrack-ng.org/doku.php?id=ipw3945](http://www.aircrack-ng.org/doku.php?id=ipw3945) . I start having issues when I am supposed to 'make' it. I am new to ubuntu and have been searching for help for awhile. I tried make SHELL=/bin/bash and that still didn't work. This is what the output reads.  Any help or suggestions would be greatly appreciated.


rog@Rog:~/ipwraw-ng$ make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.38-8-generic/build M=/home/rog/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

CC [M] /home/rog/ipwraw-ng/ipwraw.o
/home/rog/ipwraw-ng/ipwraw.c:43:27: fatal error: net/ieee80211.h: No such file or directory
compilation terminated.
make[2]: *** [/home/rog/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/rog/ipwraw-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [modules] Error 2
rog@Rog:~/ipwraw-ng$

---

