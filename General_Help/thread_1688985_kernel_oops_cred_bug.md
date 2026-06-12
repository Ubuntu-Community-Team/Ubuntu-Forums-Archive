---
title: "kernel oops cred bug"
date: 2011-02-16
forum: General Help
---

### Post by ajithabraham.m on 2011-02-16
hi
  i got an error on compelling kernel 2.6, i think it's a cred error,  the error is get when i tried to patch kernel with kerrighed 3.0

  VDSOSYM arch/x86/vdso/vdso-syms.lds
  LD      arch/x86/vdso/built-in.o
  CC      kerrighed/proc/remote_cred.o
cc1: warnings being treated as errors
/home/cluster/soft/kerrighed-src/_kernel/include/linux/cred.h: In function 'get_cred':
/home/cluster/soft/kerrighed-src/_kernel/include/linux/cred.h:189:  warning: passing argument 1 of 'get_new_cred' discards qualifiers from  pointer target type
make[7]: *** [kerrighed/proc/remote_cred.o] Error 1
make[6]: *** [kerrighed/proc] Error 2
make[5]: *** [kerrighed] Error 2
make[4]: *** [sub-make] Error 2
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/cluster/soft/kerrighed-src/kernel'
make[2]: *** [kernel] Error 2
make[2]: Leaving directory `/home/cluster/soft/kerrighed-src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/cluster/soft/kerrighed-src'
make: *** [all] Error 2


thanks

---

