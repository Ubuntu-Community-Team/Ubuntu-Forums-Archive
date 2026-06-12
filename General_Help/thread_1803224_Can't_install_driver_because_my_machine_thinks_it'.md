---
title: "Can't install driver because my machine thinks it's 64 bit"
date: 2011-07-13
forum: General Help
---

### Post by mtcougar832 on 2011-07-13
I have an older Pentium 4 machine. I'm trying to get 3-D by installing the NVIDIA driver. However, the 32 bit driver won't install because my machine thinks it is running x86_64. I was under the impression that a 32-bit pc could not run a 64 bit OS?

[snipped] cat /proc/cpu
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping	: 5
cpu MHz		: 3200.132
cache size	: 2048 KB

```

uname -a
```
Linux pegasus 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

How do I fix this?

*PS - I tried installing an NVIDIA driver from synaptic, but stopped when it wanted to remove xorg.*

---

### Post by Bucky Ball on 2011-07-13
Install the 32bit Ubuntu! I'm not sure how this could have happened but sure looks like you have the 64bit installed.

Maybe a wiser head can fill us in.

> ... x86_64 GNU/Linux

---

### Post by CatKiller on 2011-07-13
> **mtcougar832 said:**
> I was under the impression that a 32-bit pc could not run a 64 bit OS?

I think that's a Cedar Mill processor, which is definitely 64-bit.

---

### Post by realzippy on 2011-07-13
Yep,it is 64 bit.
Anyway,suggest to install the nvidia-driver with the additional drivers tool,so you won't have to care about it.

---

