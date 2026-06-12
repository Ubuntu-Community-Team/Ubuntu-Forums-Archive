---
title: "kernel compile problem"
date: 2009-11-09
forum: General Help
---

### Post by weishigoname on 2009-11-09
I am using ubuntu 9.04 .When I use "make ARCH=arm menuconfig " to compile linux-2.4.20 kernel ,I got a problem below:
                   
 ws@ws-desktop:~/download/kernel/linux-2.4.20$ make ARCH=arm menuconfig
rm -f include/asm-arm/arch include/asm-arm/proc
(cd include/asm-arm; ln -sf arch- arch; ln -sf proc- proc)
rm -f include/asm
( cd include ; ln -sf asm-arm asm)
make -C scripts/lxdialog all
make[1]: Entering directory `/home/ws/download/kernel/linux-2.4.20/scripts/lxdialog'
make[1]: Leaving directory `/home/ws/download/kernel/linux-2.4.20/scripts/lxdialog'
/bin/bash scripts/Menuconfig arch/arm/config.in
Using defaults found in arch/arm/defconfig
Preparing scripts: functions, parsingscripts/Menuconfig: line 700:  9732 Killed                  awk "$1"
Awk died with error code 137. Giving up.
make: *** [menuconfig] Error 1

scripts/Menuconfig :line 700 is callawk() function

---

### Post by falconindy on 2009-11-09
Are you trying to cross compile? Do you have the appropriate libraries to do so?

---

### Post by weishigoname on 2009-11-11
> **falconindy said:**
> Are you trying to cross compile? Do you have the appropriate libraries to do so?
I use cross_compile arm-linux-gcc 3..3.2 to compile ,the problem is the same.And I try "make menuconfig" ,it works.I try "make ARCH=arm CROSS_COMPILE=arm-linux- menuconfig" to compile kernel-2.6.31.4,it works,and I try another --kernel-2.4.37.7 using  "make ARCH=arm CROSS_COMPILE=arm-linux- menuconfig" ,it get problem too,but it is not the same problem.

---

