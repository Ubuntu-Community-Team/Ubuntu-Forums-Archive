---
title: "octeon-sdk"
date: 2010-01-11
forum: General Help
---

### Post by alanc_yang on 2010-01-11
wonder have people tried install octeon-sdk, and cross compiled linux kernel for octeon evaluation board successfully (any environment variables besides sdk is needed, for instance) could shed some light.  thanks in advance.

---

### Post by alanc_yang on 2010-01-11
encountered the following error, wonder how to work around:
---
alan@alan-laptop:/usr/local/Cavium_Networks/OCTEON-SDK/linux$ sudo make -s kernel
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
In file included from include/linux/cpumask.h:84,
                 from include/asm/processor.h:14,
                 from include/asm/thread_info.h:15,
                 from include/linux/thread_info.h:21,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:7,
                 from include/linux/stat.h:57,
                 from include/linux/compat.h:10,
                 from arch/mips/kernel/asm-offsets.c:11:
include/linux/kernel.h:10:20: error: stdarg.h: No such file or directory
In file included from include/linux/cpumask.h:84,
                 from include/asm/processor.h:14,
                 from include/asm/thread_info.h:15,
                 from include/linux/thread_info.h:21,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:7,
                 from include/linux/stat.h:57,
                 from include/linux/compat.h:10,
                 from arch/mips/kernel/asm-offsets.c:11:
include/linux/kernel.h:112: error: expected declaration specifiers or '...' before 'va_list'
include/linux/kernel.h:116: error: expected declaration specifiers or '...' before 'va_list'
include/linux/kernel.h:120: error: expected declaration specifiers or '...' before 'va_list'
include/linux/kernel.h:127: error: expected declaration specifiers or '...' before 'va_list'
include/linux/kernel.h:143: error: expected declaration specifiers or '...' before 'va_list'
make[3]: *** [arch/mips/kernel/asm-offsets.s] Error 1
make[2]: *** [prepare0] Error 2
make[1]: *** [linux] Error 2
make: *** [kernel] Error 2

---

### Post by alanc_yang on 2010-01-12
from su, it encounters some other errors.  wonder people could shed some light how to work around.

--- 
root@alan-laptop:/usr/local/Cavium_Networks/OCTEON-SDK/linux# make  -s kernel
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
scripts/mod/modpost.c: In function ‘check_sec_ref’:
scripts/mod/modpost.c:849: warning: ‘r.r_info’ may be used uninitialized in this function
scripts/mod/sumversion.c: In function ‘get_src_version’:
scripts/mod/sumversion.c:384: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/mod/sumversion.c:384: error: (Each undeclared identifier is reported only once
scripts/mod/sumversion.c:384: error: for each function it appears in.)
scripts/mod/sumversion.c:384: warning: unused variable ‘filelist’
make[4]: *** [scripts/mod/sumversion.o] Error 1
make[3]: *** [scripts/mod] Error 2
make[2]: *** [scripts] Error 2
make[1]: *** [linux] Error 2
make: *** [kernel] Error 2

---

### Post by alanc_yang on 2010-01-12
add #include <limits.h> in sumversion.c file solved the problem.

---

