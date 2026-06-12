---
title: "Cannot find -lpcre"
date: 2010-04-27
forum: General Help
---

### Post by wingmir on 2010-04-27
HI, 

I am trying to install lighttpd into ubuntu with arm.

BUT when I configure the file, it gives out an error!

root@ubuntu:~/Desktop/lighttpd-1.4.26# make
..............................
..............................
[SIZE=3]
/home/wing/embest/arm-2007q3/bin/../lib/gcc/arm-none-linux-gnueabi/4.2.1/../../../../arm-none-linux-gnueabi/bin/ld: warning: library search path "/usr/lib" is unsafe for cross-compilation
/home/wing/embest/arm-2007q3/bin/../lib/gcc/arm-none-linux-gnueabi/4.2.1/../../../../arm-none-linux-gnueabi/bin/ld: skipping incompatible /usr/lib/libpcre.so when searching for -lpcre
/home/wing/embest/arm-2007q3/bin/../lib/gcc/arm-none-linux-gnueabi/4.2.1/../../../../arm-none-linux-gnueabi/bin/ld: skipping incompatible /usr/lib/libpcre.a when searching for -lpcre
/home/wing/embest/arm-2007q3/bin/../lib/gcc/arm-none-linux-gnueabi/4.2.1/../../../../arm-none-linux-gnueabi/bin/ld: [COLOR=Red]cannot find -lpcre[/COLOR]
collect2: ld returned 1 exit status[/SIZE]
make[3]: *** [lighttpd] Error 1
make[3]: Leaving directory `/root/Desktop/lighttpd-1.4.26/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/Desktop/lighttpd-1.4.26/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/Desktop/lighttpd-1.4.26'
make: *** [all] Error 2


I know there is very simple mistake.However, I still don`t know how to fix it! It is so urgent. Can anyone help to solve it? 

Thx a lot !

---

### Post by lisati on 2010-04-27
Moved from FF&H to "General Help"

---

