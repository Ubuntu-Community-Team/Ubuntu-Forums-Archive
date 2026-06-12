---
title: "Gimp segfault jaunty"
date: 2009-08-05
forum: General Help
---

### Post by gurpal2000 on 2009-08-05
gimp-2.6[7856]: segfault at 0 ip 083373ce sp bfb85020 error 4 in gimp-2.6[8048000+411000]

kernel - 2.6.28-14-generic

Any ideas how to get GIMP working?

Thanks

---

### Post by gurpal2000 on 2009-08-05
> **gurpal2000 said:**
> gimp-2.6[7856]: segfault at 0 ip 083373ce sp bfb85020 error 4 in gimp-2.6[8048000+411000]

kernel - 2.6.28-14-generic

Any ideas how to get GIMP working?

Thanks

ah replying to my own: new to linux and someone mentioned running with gdb:

```

Starting program: /usr/bin/gimp-2.6 
[Thread debugging using libthread_db enabled]
[New Thread 0xb716c710 (LWP 9754)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb716c710 (LWP 9754)]
gimp_font_list_restore (list=0x8c21110)
    at /build/buildd/gimp-2.6.6/./app/text/gimpfontlist.c:240
240    /build/buildd/gimp-2.6.6/./app/text/gimpfontlist.c: No such file or directory.
    in /build/buildd/gimp-2.6.6/./app/text/gimpfontlist.c

```

---

### Post by gurpal2000 on 2009-08-19
bump - any ideas?

---

### Post by gurpal2000 on 2009-09-14
> **gurpal2000 said:**
> bump - any ideas?

Ended up reinstalling libfont* fontconfig* and all is well.

---

