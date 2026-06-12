---
title: "Trying to compile kernel, hang on patch -p1"
date: 2012-04-19
forum: General Help
---

### Post by Hungry Man on 2012-04-19
edit: Solved.

---

### Post by Hungry Man on 2012-04-19
I seem to have gotten beyond there and I've configured the kernel with pax etc

now I get 


Your gcc installation does not support plugins.  If the necessary headers for plugin support are missing, they should be installed.  On Debian, apt-get install gcc-<ver>-plugin-dev.  If you choose to ignore this error and lessen the improvements provided by this patch, re-run make with the DISABLE_PAX_PLUGINS=y argument..  Stop.

when I try "make"

edit: fixed

now


In file included from include/linux/thread_info.h:53:0,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/mmzone.h:7,
                 from include/linux/gfp.h:4,
                 from include/linux/slab.h:12,
                 from include/linux/crypto.h:23,
                 from arch/x86/kernel/asm-offsets.c:8:
/usr/src/linux/linux-3.2.15/arch/x86/include/asm/thread_info.h: At top level:
/usr/src/linux/linux-3.2.15/arch/x86/include/asm/thread_info.h:214:35: error: redefinition of &#8216;current_thread_info&#8217;
/usr/src/linux/linux-3.2.15/arch/x86/include/asm/thread_info.h:184:44: note: previous definition of &#8216;current_thread_info&#8217; was here
/usr/src/linux/linux-3.2.15/arch/x86/include/asm/thread_info.h: In function &#8216;current_thread_info&#8217;:
/usr/src/linux/linux-3.2.15/arch/x86/include/asm/thread_info.h:218:9: error: &#8216;KERNEL_STACK_OFFSET&#8217; undeclared (first use in this function)
/usr/src/linux/linux-3.2.15/arch/x86/include/asm/thread_info.h:218:9: note: each undeclared identifier is reported only once for each function it appears in
arch/x86/kernel/asm-offsets.c: In function &#8216;common&#8217;:
arch/x86/kernel/asm-offsets.c:36:2: error: &#8216;struct thread_info&#8217; has no member named &#8216;lowest_stack&#8217;
cc1: some warnings being treated as errors
make[1]: *** [arch/x86/kernel/asm-offsets.s] Error 1
make: *** [prepare0] Error 2

---

