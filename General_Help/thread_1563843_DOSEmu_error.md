---
title: "DOSEmu error"
date: 2010-08-29
forum: General Help
---

### Post by me239 on 2010-08-29
It's been awhile now since I installed my first Ubuntu (9.04) and to see how far its come brings me joy, however support for some of my applications is fading. I've been using DOSEmu since the first day I installed Ubuntu and never had a problem until now. Just yesterday I decided to upgrade to 10.4 thinking its everything I already had plus more. I was wrong. Several of my applications no longer run or have error messages. The error message I get with DOSEmu is the following, 

[B][I]ERROR: general protection at 0x76720: 8
ERROR: general protection at 0x76720: 8
Program=do_vm86.c, Line=291[/I][/B]

If anyone could help me get my computer back to the way it was without downgrading, it would be greatly appreciated :)

---

### Post by jamillikan on 2010-09-06
I believe it's a kernel problem.  I, too, have to stay stuck at 2.6.27-11; otherwise I have regressions in my dos applications.  Kernels 2.6.28 and beyond cause segfaults in my applications.  Too bad nobody cares, but I'm just resigned to that fact that's the way it is.  I'm just glad I have the complete 8.10 repositories as well as the 9.04 ones.  We will just have to remain where we are without going forward.

I would love to use 10.04 but it's not going to happen because of the aforementioned regression.

---

### Post by emendelson on 2010-09-06
This error doesn't occur on a clean install of 10.4. For some general advice on running DOSEMU in Ubuntu (specifically for running WordPerfect for DOS), see:

[http://wpdos.org/linux.html](http://wpdos.org/linux.html)

---

### Post by jamillikan on 2010-09-10
Ahem...excuse me.  No.  It still doesn't work even with a clean install.  Segfaults on one critical DOS application.

---

