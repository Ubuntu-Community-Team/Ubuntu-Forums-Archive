---
title: "report kernel oops"
date: 2009-10-30
forum: General Help
---

### Post by jmore9 on 2009-10-30
I have been tring to report a kernel oops all day long.

One time launchpad says too much text then another i don't include enought.

Any one have an easy way of posting this kernel error with the associated 
logs ?

Thanks in advance

---

### Post by cariboo on 2009-10-30
This really isn't the right place for your question. but if you are try to create a bug about the ECC error you should be able to add you name to the [b]Affects me to[list], by search for an ECC error bug on launchpad.

You can also use :

```
apport-gtk
```

to report it.

---

### Post by jmore9 on 2009-10-31
Yes that is what i was trying to remeber!  Thanks

---

### Post by ajithabraham.m on 2011-02-15
hi
  i got an error on compelling kernel 2.6, i think it's a cred error, the error is get when i tried to patch kernel with kerrighed 3.0

  VDSOSYM arch/x86/vdso/vdso-syms.lds
  LD      arch/x86/vdso/built-in.o
  CC      kerrighed/proc/remote_cred.o
cc1: warnings being treated as errors
/home/cluster/soft/kerrighed-src/_kernel/include/linux/cred.h: In function 'get_cred':
/home/cluster/soft/kerrighed-src/_kernel/include/linux/cred.h:189: warning: passing argument 1 of 'get_new_cred' discards qualifiers from pointer target type
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

### Post by uRock on 2011-02-15
This thread is more than a year old, please start a new one.

Thread Closed.

---

