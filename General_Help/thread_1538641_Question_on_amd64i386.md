---
title: "Question on amd64/i386"
date: 2010-07-25
forum: General Help
---

### Post by elys22 on 2010-07-25
I couldn't remember which of these I had, so I tried finding out from the terminal, and got this:

> manda@mandas-pc:~$ uname -r
2.6.31-21-generic


Can anyone tell me what that means? I want to do a clean install of Lucid but I don't remember whether I need an ISO for amd64 or i386. Can anyone shed some light on this?

---

### Post by CharlesA on 2010-07-25
Try running this:

```
uname -a
```

---

### Post by Bachstelze on 2010-07-25
The kernel version is the same for i386 and amd64.  Use [font=monospace]uname -m[/font].

---

### Post by elys22 on 2010-07-25
Tried both suggestions and got this:

> manda@mandas-pc:~$ uname -a
Linux mandas-pc 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux
manda@mandas-pc:~$ uname -m
x86_64

So... are you saying it doesn't matter which version I download? I'm wondering if the terminal is just telling me which version of Ubuntu I have installed (generic for either?) instead of which is more compatible with my machine.

---

### Post by Bachstelze on 2010-07-25
> **elys22 said:**
> 
So... are you saying it doesn't matter which version I download? I'm wondering if the terminal is just telling me which version of Ubuntu I have installed (generic for either?) instead of which is more compatible with my machine.

It's telling you which version of the *kernel* you have installed.  As I said, the i386 and amd64 versions of Ubuntu use the same kernel version.  Your machine is amd64.

---

### Post by elys22 on 2010-07-25
Ah, okay, thank you. Much love.

---

### Post by egalvan on 2010-07-25
> **Bachstelze said:**
>  As I said, the i386 and amd64 versions of Ubuntu **use the same kernel version**. .

I'm a bit confused...

Are you saying that 32bit and 64bit use the **same** kernel?

or that they use the same version **number** ?



(I always understood that 32bit & 64bit software was compiled with different compiler flags)

---

### Post by egalvan on 2010-07-25
> **elys22 said:**
> 
So... are you saying it doesn't matter which version I download? 
instead of which is more compatible with my machine.

Your machine is 64bit, which means it can run both 32bit *and* 64bit software.

64bit will be a tad bit more "compatible".
It will take full advantage of the capabilities of the 64bit hardware.
It will (usually) be faster.

Adobe Flash is problematic at the moment...
Adobe had removed the 64bit version a week or two ago...
I don't know if it's back...

Not much else has problems.
64bit has been very stable for quite some time.


I would recommend 64bit, unless Adobe Flash is a "must-have" for you.

It's not for me, so I run 64bit.

---

### Post by Bachstelze on 2010-07-25
> **egalvan said:**
> 
Are you saying that 32bit and 64bit use the **same** kernel?

or that they use the same version **number** ?

Same version number, of course.  My point was that since [font=monospace]uname -r[/font] only prints the kernel version number, you can't use it to tell an amd64 system from an i386 one.

---

### Post by bakegoodz on 2010-07-25
Sorry if this sound redundant, but it didn't seem like it was made clear. 32 bit and 64 bit kernels are different, but they can certainly have the same version since the version numbers are applied to the source code. The source code can then be compiled into working machine code for the intended processor, such as Power PC, i386, AM64, ARM, etc
AMD64 processors can also run kernels compiled for i386 too
i386 processors can't run AMD64 kernels
Your "uname -a" command told us you have a kernel compiled for AMD64
You can find details of your processor with "cat /proc/cpuinfo"

---

