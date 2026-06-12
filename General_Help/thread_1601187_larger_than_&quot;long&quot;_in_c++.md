---
title: "larger than &quot;long&quot; in c++"
date: 2010-10-19
forum: General Help
---

### Post by fantastic on 2010-10-19
What is larger than a long in C++ and how do I include that?

(Sorry, I'm not a big C/C++ user).

---

### Post by BrockStrongo on 2010-10-19
I'm very new to C but doesn't double hold like 28 digits? what about double long?
Again I am just learning.
but maybe try float or even long long.
according to [www.frihost.com/forums/vt-30851.html](www.frihost.com/forums/vt-30851.html) long long might work.
sorry if this is all wrong and useless.

---

### Post by BrockStrongo on 2010-10-19
sorry for the ramble, try long long

---

### Post by ender4 on 2010-10-20
It depends on a lot of things, including architecture and compiler.  long long is at least as large as long, but can actually be the same size.  (I actually think that long long is the same as long with gcc on a 64 bit machine, though I could be wrong).  For better control use "stdint.h" which provides types such as int64_t (signed 64 bit) and uint64_t.  A double can hold larger numbers than any integer type, but it is susceptible to round-off error, and you lose some accuracy in some cases.  

If you need really big integer's with full precision you might want to use an arbitrary precision library.

---

### Post by fantastic on 2010-10-20
Thanks guys.

I wonder if part of my problem is using Eclipse.

I added the "-std=c99" declaration into the C++ compiler settings, but I don't think it's working properly (due to probably another error on my part).

Is there something besides Eclipse, or VIM, that I can use?

---

### Post by fantastic on 2010-10-20
> **fantastic said:**
> Thanks guys.

I wonder if part of my problem is using Eclipse.

I added the "-std=c99" declaration into the C++ compiler settings, but I don't think it's working properly (due to probably another error on my part).

Is there something besides Eclipse, or VIM, that I can use?

For future note, I tried NetBeans. Works great!

For large numbers I downloaded the c++ BigInt from [SourceForge]("http://sourceforge.net/projects/cpp-bigint/").

---

