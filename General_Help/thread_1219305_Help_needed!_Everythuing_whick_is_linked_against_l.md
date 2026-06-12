---
title: "Help needed! Everythuing whick is linked against libgio-2.0.so is core dumping!"
date: 2009-07-21
forum: General Help
---

### Post by rainefan on 2009-07-21
Hi ppl! I need your help!

Recently I've updated to latest kernel 2.6.28-14-generic i686 in my Jaunty Jackalope 32-bit system.

I use kde4 4.3 RC and in the latest days I've been suffering of massive core dumping due to 'segmentation fault' my applications that depend on Gnome libs.

My thunderbird can't even save an attachment, it just cores dump :frown:

I've tried gedit from console, it cores dump even before starting!

Here is the backtrace of gdb on gedit behavior:

```

(gdb) bt
#0  0x00000000 in ?? ()
#1  0xb790cd9d in ?? () from /usr/lib/libgio-2.0.so.0
#2  0xb78e58b2 in ?? () from /usr/lib/libgio-2.0.so.0
#3  0xb78f92f9 in ?? () from /usr/lib/libgio-2.0.so.0
#4  0xb78f2204 in ?? () from /usr/lib/libgio-2.0.so.0
#5  0xb7738e26 in ?? () from /usr/lib/libglib-2.0.so.0
#6  0xb77377bf in ?? () from /usr/lib/libglib-2.0.so.0
#7  0xb76b04ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0

```

From my thunderbird launched on console:
$ /usr/lib/thunderbird/thunderbird

```

#0  0xb808e430 in __kernel_vsyscall ()
#1  0xb7ec74b0 in raise () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08057c3e in ?? ()
#3  <signal handler called>
#4  0xb4132a52 in ?? ()
#5  0xb79ebd9d in ?? () from /usr/lib/libgio-2.0.so.0
#6  0xb79c48b2 in ?? () from /usr/lib/libgio-2.0.so.0
#7  0xb79d82f9 in ?? () from /usr/lib/libgio-2.0.so.0
#8  0xb79d1204 in ?? () from /usr/lib/libgio-2.0.so.0
#9  0xb77a5e26 in ?? () from /usr/lib/libglib-2.0.so.0
#10 0xb77a47bf in ?? () from /usr/lib/libglib-2.0.so.0
#11 0xb7ebf4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb74a749e in clone () from /lib/tls/i686/cmov/libc.so.6

```

As you can see something in libgio-2.0.so is wrong. Maybe some new bug due to latest kernel patch (that nasty bug on NULL pointers stuff).

**Interesting part:**
if open gedit with gksudo it just works witout any core dump!
```
gksudo gedit
```

Any help?

Thanks and regards!
Raine

---

### Post by rainefan on 2009-07-21
Well, I've posted a bug report here:
[https://bugs.launchpad.net/ubuntu/+bug/402693](https://bugs.launchpad.net/ubuntu/+bug/402693)

---

### Post by rainefan on 2009-08-25
Workaround here: [https://bugs.launchpad.net/ubuntu/+bug/402693](https://bugs.launchpad.net/ubuntu/+bug/402693)

Raine

---

