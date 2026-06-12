---
title: "kernel compiling problem"
date: 2006-02-08
forum: General Help
---

### Post by evilgold on 2006-02-08
I'm trying to compile kernel 2.4.20 with open mosix support, I keep getting this when i run "make dep bzImage modules modules_install"

```
In file included from /usr/src/linux-2.4.20/include/linux/kernel.h:15,
                 from /usr/src/linux-2.4.20/include/linux/wait.h:13,
                 from /usr/src/linux-2.4.20/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.20/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.20/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.20/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.20/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.20/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.20/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.20/include/asm/byteorder.h:14: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.20/include/asm/byteorder.h:28: warning: type qualifiers ignored on function return type
In file included from /usr/src/linux-2.4.20/include/linux/byteorder/little_endian.h:11,
                 from /usr/src/linux-2.4.20/include/asm/byteorder.h:45,
                 from /usr/src/linux-2.4.20/include/linux/kernel.h:15,
                 from /usr/src/linux-2.4.20/include/linux/wait.h:13,
                 from /usr/src/linux-2.4.20/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.20/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.20/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.20/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.20/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.20/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.20/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.20/include/linux/byteorder/swab.h:160: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.20/include/linux/byteorder/swab.h:173: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.20/include/linux/byteorder/swab.h:186: warning: type qualifiers ignored on function return type
/usr/src/linux-2.4.20/include/linux/byteorder/swab.h:200: warning: type qualifiers ignored on function return type
In file included from /usr/src/linux-2.4.20/include/linux/prefetch.h:13,
                 from /usr/src/linux-2.4.20/include/linux/list.h:6,
                 from /usr/src/linux-2.4.20/include/linux/wait.h:14,
                 from /usr/src/linux-2.4.20/include/linux/fs.h:12,
                 from /usr/src/linux-2.4.20/include/linux/capability.h:17,
                 from /usr/src/linux-2.4.20/include/linux/binfmts.h:5,
                 from /usr/src/linux-2.4.20/include/linux/sched.h:9,
                 from /usr/src/linux-2.4.20/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.20/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.20/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.20/include/asm/processor.h:74: error: array type has incomplete element type
In file included from /usr/src/linux-2.4.20/include/hpc/hpctask.h:13,
                 from /usr/src/linux-2.4.20/include/linux/sched.h:33,
                 from /usr/src/linux-2.4.20/include/linux/mm.h:4,
                 from /usr/src/linux-2.4.20/include/linux/slab.h:14,
                 from /usr/src/linux-2.4.20/include/linux/proc_fs.h:5,
                 from init/main.c:15:
/usr/src/linux-2.4.20/include/hpc/defs.h:86: error: array type has incomplete element type
In file included from /usr/src/linux-2.4.20/include/linux/unistd.h:9,
                 from init/main.c:17:
/usr/src/linux-2.4.20/include/asm/unistd.h:375: warning: conflicting types for built-in function ‘_exit’
make: *** [init/main.o] Error 1

```

Could anyone tell me how i fix this? Do i have somthing setup wrong, or do i need to use an older version of gcc to compile it.

Thanks

---

### Post by ctg60 on 2007-12-02
You can use older versions of gcc, e.g. gcc 2.95 gcc 3.x to compile your kernel instead of gcc 4.x

---

