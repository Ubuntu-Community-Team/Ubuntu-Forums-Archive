---
title: "64 bits or 32 bits?"
date: 2009-09-10
forum: General Help
---

### Post by sopadeajo on 2009-09-10
Where can i know if my ubuntu 9.04 is architectured with 32 bits or 64 bits and my old Pentium D 3.Ghz? I know only a few applications or programs are optimised for 64 bits, so it is probably not so important (I have only heard of a few sieve mathematical programs for finding huge prime numbers are optimised for 64 bits).

---

### Post by akakingess on 2009-09-10
I don't know if you are just trying to figure out whether your current installation of Ubuntu is 32 or 64, in that case```
uname -a
```
should tell you which version is installed and running (if you see x86_64, obviously that is the 64-bit version). Sorry if this was not what you were asking, just trying to offer some assistance.

---

### Post by sopadeajo on 2009-09-10
Thanks but i do not see information of if it is running on 32 or 64 bits:

"Linux **-desktop 2.6.28-15-generic #49-Ubuntu SMP ....."

---

### Post by earthpigg on 2009-09-10
> **sopadeajo said:**
> Thanks but i do not see information of if it is running on 32 or 64 bits:

"Linux **-desktop 2.6.28-15-generic #49-Ubuntu SMP ....."

lol, post the whole thing and we will tell you which line it is that tells you :D

---

### Post by akakingess on 2009-09-10
Thanks earthpigg, I thought I was losing my mind, cuz I was pulling that command from memory, but that should tell us.

---

### Post by sopadeajo on 2009-09-13
Linux **-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux  So 32 or 64 bits??

---

### Post by Topsiho on 2009-09-13
I have the 64 bits version and get:

Linux hostname 2.6.24-24-generic #1 SMP Tue Aug 18 16:22:17 UTC 2009 x86_64 GNU/Linux

so ... :)

Topsiho

I forgot to say I have Ubuntu 8.04 on this box.

---

### Post by biebel on 2009-09-13
That is 32 bit.

64 bit would give x86_64 GNU/Linux @ the end of the line afaik.

---

### Post by earthpigg on 2009-09-13
> **sopadeajo said:**
> Linux **-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 _***i686***_ GNU/Linux

i_86 (the _ can be anything, such as i_***6***_86 in your case)
x86

linux words for 32 bit 


amd64
x86_64

linux words for 64 bit :D

---

