---
title: "Wifi Card Driver Installation Error - AWLL5088 Airlink 101"
date: 2011-09-30
forum: General Help
---

### Post by ssharma286 on 2011-09-30
Okay so far I have downloaded the file from the Realtek website. I have put the folder in usr/src/ and I have made it executable. I have ran it in sudo terminal (if thats what you call it, I am a newbie to Ubuntu ;O) and after doing this I am getting the error message below...I couldn't find a solution through google so I thought I'd give the forum a try.

```
		Auto install for 8192cu
		September, 1 2010 v 1.0.0
cd: 7: can't cd to driver
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
linux-headers-2.6.38-11
linux-headers-2.6.38-11-generic
linux-headers-2.6.38-8
linux-headers-2.6.38-8-generic
RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922
Authentication requested [root] for make driver:
[: 18: unexpected operator
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf --silentoldconfig Kconfig
***
*** Configuration file ".config" not found!
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.
Compile make driver error: 2, Please check error Mesg

```

---

