---
title: "Compiling Kernel 2.6.30.5"
date: 2009-09-08
forum: General Help
---

### Post by piperdown10 on 2009-09-08
Hey all. I'm in the process of compiling my own kernel and have come across an error. I've been following [this tutorial]("http://www.linuxforums.org/articles/the-newbies-guide-to-compiling-your-first-kernel_272.html") and when I get to *make xconfig* I receive this:

```
root@location:/usr/src/linux-headers-2.6.28-15-generic# make xconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  CHECK   qt
*
* Unable to find the QT3 installation. Please make sure that
* the QT3 development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function &#8216;conf_askvalue&#8217;:
scripts/kconfig/conf.c:104: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function &#8216;conf_choice&#8217;:
scripts/kconfig/conf.c:306: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
make[1]: *** No rule to make target `scripts/kconfig/.tmp_qtcheck', needed by `scripts/kconfig/qconf.o'.  Stop.
make: *** [xconfig] Error 2

```

What is QT3 and is that what's causing the error?

Thanks!

---

### Post by Bachstelze on 2009-09-08
This tutorial is not very good... Better use [that one]("http://ubuntuforums.org/showthread.php?t=311158").

---

### Post by piperdown10 on 2009-09-08
Wow! That's much better. Thank you. :KS

---

