---
title: "SESC installationon Ubuntu 10.04. &quot;echo -EB unrecognised&quot;"
date: 2011-04-26
forum: General Help
---

### Post by aravindreddy on 2011-04-26
Hi All

I am trying to install SESC simulator on my AMD64 machine with Ubuntu 10.04.
As recommended I have installed the suitable gcc-3.4 and bison versions.
I have been following the instructions provided by 
[http://manio.org/sesc-tutorial-1-instaall-whole-sesc-step-by-step-577.html](http://manio.org/sesc-tutorial-1-instaall-whole-sesc-step-by-step-577.html)

When I try to build build-2-gcc-core. I get the following error:
.
...
.....
[I]cat /home/anusha/sescutils/src/gcc-3.4/gcc/gcc/config/fp-bit.c >> dp-bit.c
/home/anusha/sescutils/build-mipseb-linux/obj/gcc-core-build/gcc/xgcc -B/home/anusha/sescutils/build-mipseb-linux/obj/gcc-core-build/gcc/ -B/home/anusha/sescutils/install/mipseb-linux/bin/ -B/home/anusha/sescutils/install/mipseb-linux/lib/ -isystem /home/anusha/sescutils/install/mipseb-linux/include -isystem /home/anusha/sescutils/install/mipseb-linux/sys-include   -fno-PIC -mno-abicalls -O2 -DIN_GCC -DCROSS_COMPILE   -W -Wall  -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes  -Wold-style-definition  -isystem ./include  -I. -I.  -I/home/anusha/sescutils/src/gcc-3.4/gcc/gcc -I/home/anusha/sescutils/src/gcc-3.4/gcc/gcc/. -I/home/anusha/sescutils/src/gcc-3.4/gcc/gcc/../include    -g0 -finhibit-size-directive -fno-inline-functions -fno-exceptions  -fno-zero-initialized-in-bss -fno-unit-at-a-time  \
       -c /home/anusha/sescutils/src/gcc-3.4/gcc/gcc/crtstuff.c -DCRT_BEGIN \
      -o crtbegin.o
[B]as: unrecognized option '-EB'
make[1]: *** [crtbegin.o] Error 1
make[1]: Leaving directory `/home/anusha/sescutils/build-[/B]**mipseb-linux/obj/gcc-core-**[B]build/gcc'
make: *** [all-gcc] Error 2[/B][/I]

Can somebody suggest me a solution for this.

Thank you in advance,
Aravind
SUNY Buffalo.

---

