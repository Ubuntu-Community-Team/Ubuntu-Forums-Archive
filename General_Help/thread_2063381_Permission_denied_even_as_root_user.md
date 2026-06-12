---
title: "Permission denied even as root user"
date: 2012-09-26
forum: General Help
---

### Post by garandcarbine on 2012-09-26
Hey guys,
  I'm trying to compile DOSBox, I type "./configure" while in the correct directory (I'm 100% positive that this is the right one, and this is all in terminal of course). But, I get this:

```
root@chris-desktop:/media/Beta/dosbox# ./configure
bash: ./configure: Permission denied

```I don't know if I'm posting this in the right section, but I'm stumped as to how it can deny permission to the root user...

  I've considered that maybe I'm doing it wrong, so if anyone whom has built DOSBox from source in Ubuntu before has any pointers, by all means. :)

---

### Post by papibe on 2012-09-26
Hi garandcarbine.

If the file does not have execution permisions, bash can't execute it.

Add execute permission to the file:
```
chmod a+x ./configure
```
and then try to execute it again.

Let us know how it goes.
Regards.

---

### Post by garandcarbine on 2012-09-27
Hi, 
  Tried what you said, here is what terminal gave me (In lieu of output after doing the configure bit, I tried to move on to the next step, exactly as the instructions said)

```
chris@chris-desktop:/media/Beta/dosbox$ chmod a+x ./configure
chris@chris-desktop:/media/Beta/dosbox$ make
make: *** No targets specified and no makefile found.  Stop.
```

EDIT: Bollocks, I copied the wrong bit. It's the correct one now, although they had the same result.

---

### Post by stepking2 on 2012-09-27
Doing the chmod command only makes the file executable, it does not run it.
Try running the configure script now, and then make.

If that doesn't work, have you tried "sh" instead of "./" ?

---

### Post by Lars Noodén on 2012-09-27
I see that the repositories have version 0.74 available.  You should be able to get it with Synaptic or the Software Center.   Is there any particular reason you are trying to compile from source instead of using the pre-packaged edition?

---

### Post by spjackson on 2012-09-27
> **Lars Noodén said:**
> I see that the repositories have version 0.74 available.  You should be able to get it with Synaptic or the Software Center.   Is there any particular reason you are trying to compile from source instead of using the pre-packaged edition?

+1. Prefer pre-built packages to compiling yourself.

If you do have a reason to compile it yourself then... Does /media/Beta/dosbox sit on a Linux native filesystem? The fact that configure is not already executable suggests that it may be on a Windows filesystem (e.g. FAT, NTFS). If you are doing that, it is probably doomed to failure. Make sure you compile Linux programs on Linux filesystems.

---

### Post by garandcarbine on 2012-09-27
> **Lars Noodén said:**
> I see that the repositories have version 0.74 available.  You should be able to get it with Synaptic or the Software Center.   Is there any particular reason you are trying to compile from source instead of using the pre-packaged edition?

Someone told me it's more likely to work if you compile it yourself, because it's configured to work with your system, or some such thing like that. And when I looked on the DOSBox website, I didn't see any builds for Ubuntu, so I thought I'd make my own.

---

### Post by garandcarbine on 2012-09-27
> **spjackson said:**
> +1. Prefer pre-built packages to compiling yourself.

If you do have a reason to compile it yourself then... Does /media/Beta/dosbox sit on a Linux native filesystem? The fact that configure is not already executable suggests that it may be on a Windows filesystem (e.g. FAT, NTFS). If you are doing that, it is probably doomed to failure. Make sure you compile Linux programs on Linux filesystems.

Yeah, it's on an NTFS filesystem from when I was running Windows 7. I'll reformat it to a Linux filesystem and try it then. If it doesn't work, then I'll look on software center.

---

### Post by garandcarbine on 2012-09-27
I got it to configure, turns out it *was* the filesystem I was compiling on. I installed SDL, and I configured DOSBox, but it gives me this when I try make:

```
root@chris-desktop:/media/Beta/dosbox# make
make  all-recursive
make[1]: Entering directory `/media/Beta/dosbox'
Making all in src
make[2]: Entering directory `/media/Beta/dosbox/src'
Making all in cpu
make[3]: Entering directory `/media/Beta/dosbox/src/cpu'
Making all in core_full
make[4]: Entering directory `/media/Beta/dosbox/src/cpu/core_full'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/media/Beta/dosbox/src/cpu/core_full'
Making all in core_normal
make[4]: Entering directory `/media/Beta/dosbox/src/cpu/core_normal'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/media/Beta/dosbox/src/cpu/core_normal'
Making all in core_dyn_x86
make[4]: Entering directory `/media/Beta/dosbox/src/cpu/core_dyn_x86'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/media/Beta/dosbox/src/cpu/core_dyn_x86'
Making all in core_dynrec
make[4]: Entering directory `/media/Beta/dosbox/src/cpu/core_dynrec'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/media/Beta/dosbox/src/cpu/core_dynrec'
make[4]: Entering directory `/media/Beta/dosbox/src/cpu'
source='callback.cpp' object='callback.o' libtool=no \
    DEPDIR=.deps depmode=none /bin/bash ../../depcomp \
    g++ -DHAVE_CONFIG_H -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -c -o callback.o callback.cpp
../../depcomp: line 611: exec: g++: not found
make[4]: *** [callback.o] Error 127
make[4]: Leaving directory `/media/Beta/dosbox/src/cpu'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/media/Beta/dosbox/src/cpu'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/media/Beta/dosbox/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/Beta/dosbox'
make: *** [all] Error 2

```

Now that, does not look good... Do I need to chmod make as well?

---

### Post by Lars Noodén on 2012-09-27
> **garandcarbine said:**
> I got it to configure, turns out it *was* the filesystem I was compiling on. I installed SDL, and I configured DOSBox, but it gives me this when I try make:

```

../../depcomp: line 611: exec: g++: not found

```


It looks like you need to add the compiler to your system.  It's added along with a lot of other things when you install the package build-essential

---

