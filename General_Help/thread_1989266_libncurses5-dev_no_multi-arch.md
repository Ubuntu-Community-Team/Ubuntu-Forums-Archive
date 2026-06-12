---
title: "libncurses5-dev no multi-arch ??"
date: 2012-05-28
forum: General Help
---

### Post by warpino on 2012-05-28
Hi there,

I need to install libncurses5-dev:i386 on Precise Pangolin 12.04.

When I try to do it apt-get wants to remove a bunch of things (gcc, g++ to mention a couple!!!).

Why can't I install it aside with x86_64 version?
Do you have any workaround to do it?

Regards,

w

---

### Post by warpino on 2012-05-28
ok, just to provide more info:

I'm trying to compile a freebasic application. I managed to get rid of most ld errors installing i386 versions of the C libraries, but I cannot solve this:

```
/ld: cannot find -lncurse
```

I also tried and download the libncurses5-dev_5.9-4_i386.deb package and extract files to the proper directory but the error is still there.

Any ideas?

---

