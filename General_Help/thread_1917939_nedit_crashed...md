---
title: "nedit crashed.."
date: 2012-01-31
forum: General Help
---

### Post by conradin on 2012-01-31
Hi all,
I was writing some code in nedit when it became unreponsive, and the classic, I haddnt saved recently. The processor decided to put 47% of its all into working nedit, and my context switches (cs) in vmstat went from about 1K, to 65K+
example:
```
$ vmstat 1 10
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0      0 1155540 152668 2104144    0    0    19    30  131   65891 29  2 68  1
 0  0      0 1152556 152668 2106976    0    0     0     0  557  67839  1  1 98  0 
...
```
and so on. 
anyhow, what I want to know is how to rescue a program when it gets in this state, and save my data. I lost code, and several hours work so Im not thrilled. But if I could learn what to do if this ever happens again, that would be great.

---

### Post by conradin on 2012-02-01
Bump.
This wasnt too catastrophic this time, but I still really want to know how to recover from a misbehaving process without data loss. Ive been reading, and many folks recommend using tools like ps, vmstat, strace, various signal commands, and so on, but Ive not found a single methodology. As in:

when this happens, do this, consider these things, heres what each option will do... As in a repeatable strategy for data recovery. 

Now that Im thinking about it rather than saying "OH Noez! My program!!" I may have been able to search for a temp file that nedit makes when you're modifying a document. I don't know if nedit does that, or how to recover that file into actual data, but it would have been better than nothing. 

The stuff Ive been reading is about identifying the misbehaving program, but not what to do after. I know nedit was screwing up. Then what?

---

