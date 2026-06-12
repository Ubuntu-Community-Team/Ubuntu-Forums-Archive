---
title: "make-kpkg strange vanilla kernel build errors"
date: 2011-04-30
forum: General Help
---

### Post by domcyrus on 2011-04-30
Hi there,

I've getting strange build errors when using make-kpkg with the latest (2.6.39-rc5) vanilla kernel.

I'm using the procedure outlined here:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

e.g.:
```
make oldconfig
CONCURRENCY_LEVEL=`getconf _NPROCESSORS_ONLN` fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```

I'm getting the following build errors:
```
  Building modules, stage 2.
  MODPOST 3053 modules
WARNING: modpost: Found 60 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      arch/x86/crypto/aesni-intel.mod.o
  CC      arch/x86/crypto/aes-x86_64.mod.o
In file included from include/asm-generic/int-ll64.h:11:0,
                 from include/asm-generic/types.h:7,
                 from /home/foobar/Kernel/linux-2.6/arch/x86/include/asm/types.h:4,
                 from include/linux/types.h:4,
                 from include/linux/list.h:4,
                 from include/linux/module.h:9,
                 from arch/x86/crypto/aesni-intel.mod.c:1:
/home/foobar/Kernel/linux-2.6/arch/x86/include/asm/bitsperlong.h:10:37: warning: include/asm-generic/bitsperlong.h is shorter than expected
In file included from /home/foobar/Kernel/linux-2.6/arch/x86/include/asm/bitsperlong.h:10:0,
                 from include/asm-generic/int-ll64.h:11,
                 from include/asm-generic/types.h:7,
                 from /home/foobar/Kernel/linux-2.6/arch/x86/include/asm/types.h:4,
                 from include/linux/types.h:4,
                 from include/linux/list.h:4,
                 from include/linux/module.h:9,
                 from arch/x86/crypto/aesni-intel.mod.c:1:
include/asm-generic/bitsperlong.h:33:1: warning: null character(s) ignored
In file included from include/linux/compiler.h:48:0,
                 from include/linux/stddef.h:4,
                 from include/linux/posix_types.h:4,
                 from include/linux/types.h:17,
                 from include/linux/list.h:4,
                 from include/linux/module.h:9,
                 from arch/x86/crypto/aesni-intel.mod.c:1:
include/linux/compiler-gcc.h:103:1: warning: null character(s) ignoredIn file included from include/linux/stddef.h:4:0,
                 from include/linux/posix_types.h:4,
                 from include/linux/types.h:17,
                 from include/linux/list.h:4,
                 from include/linux/module.h:9,
                 from arch/x86/crypto/aes-x86_64.mod.c:1:
include/linux/compiler.h:312:1: warning: null character(s) ignored

In file included from include/linux/stddef.h:4:0,
                 from include/linux/posix_types.h:4,
                 from include/linux/types.h:17,
                 from include/linux/list.h:4,
                 from include/linux/module.h:9,
                 from arch/x86/crypto/aes-x86_64.mod.c:1:
include/linux/compiler.h:312:3661: error: stray ‘\235’ in program
include/linux/compiler.h:312:3663: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘}’ tokenIn file included from include/linux/compiler.h:48:0,
                 from include/linux/stddef.h:4,
                 from include/linux/posix_types.h:4,
                 from include/linux/types.h:17,
                 from include/linux/list.h:4,
                 from include/linux/module.h:9,
                 from arch/x86/crypto/aesni-intel.mod.c:1:
include/linux/compiler-gcc.h:103:455: error: stray ‘\377’ in program

include/linux/compiler-gcc.h:103:455: error: stray ‘\22’ in program
include/linux/compiler-gcc.h:103:455: error: stray ‘\20’ in program
include/linux/compiler-gcc.h:103:455: error: stray ‘\10’ in program
include/linux/compiler-gcc.h:103:462: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘hY’
include/linux/compiler-gcc.h:103:462: error: stray ‘\261’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘`’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\7’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\302’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\271’ in programinclude/linux/compiler.h:312:3663: error: stray ‘\251’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\25’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\302’ in program

include/linux/compiler-gcc.h:103:462: error: stray ‘\3’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\222’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\371’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\244’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\251’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\244’ in program
include/linux/compiler.h:312:3663: error: stray ‘\301’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\360’ in program
include/linux/compiler.h:312:3667: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘.’ tokeninclude/linux/compiler-gcc.h:103:462: error: stray ‘\306’ in program

include/linux/compiler.h:312:3667: error: stray ‘\346’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\232’ in program

include/linux/compiler.h:312:3667: error: stray ‘\272’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\345’ in program

include/linux/compiler.h:312:3667: error: stray ‘\357’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\325’ in program

include/linux/compiler.h:312:3667: error: stray ‘\270’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\261’ in program

include/linux/compiler.h:312:3667: error: stray ‘\22’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\302’ in program

include/linux/compiler.h:312:3667: error: stray ‘\326’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\3’ in program
include/linux/compiler.h:312:3667: error: stray ‘\314’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\222’ in program
include/linux/compiler.h:312:3667: error: stray ‘\23’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\371’ in program
include/linux/compiler.h:312:3667: error: stray ‘\326’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\244’ in program

include/linux/compiler.h:312:3667: error: stray ‘#’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\251’ in program
include/linux/compiler.h:312:3667: error: stray ‘\320’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\244’ in program
include/linux/compiler.h:312:3667: error: stray ‘\215’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\360’ in program

include/linux/compiler.h:312:3667: error: stray ‘\344’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\306’ in program

include/linux/compiler.h:312:3667: error: stray ‘@’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\232’ in program
include/linux/compiler.h:312:3667: error: stray ‘\177’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\345’ in program
include/linux/compiler.h:312:3667: error: stray ‘\325’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\325’ in program
include/linux/compiler.h:312:3667: error: stray ‘\300’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\261’ in program

include/linux/compiler.h:312:3667: error: stray ‘\225’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\302’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\3’ in program
include/linux/compiler.h:312:3667: error: stray ‘\326’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\222’ in program
include/linux/compiler.h:312:3667: error: stray ‘\314’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\371’ in program
include/linux/compiler.h:312:3667: error: stray ‘\23’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\244’ in program
include/linux/compiler.h:312:3667: error: stray ‘\326’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\251’ in program
include/linux/compiler.h:312:3667: error: stray ‘#’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\244’ in program
include/linux/compiler.h:312:3667: error: stray ‘\320’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\360’ in program
include/linux/compiler.h:312:3667: error: stray ‘\215’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\306’ in program
include/linux/compiler.h:312:3667: error: stray ‘\344’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\232’ in program
include/linux/compiler.h:312:3667: error: stray ‘@’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\345’ in program
include/linux/compiler.h:312:3667: error: stray ‘\177’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\325’ in program
include/linux/compiler.h:312:3667: error: stray ‘\325’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\261’ in program

include/linux/compiler.h:312:3667: error: stray ‘\300’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\302’ in program

include/linux/compiler.h:312:3667: error: stray ‘\225’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\3’ in program
include/linux/compiler.h:312:3667: error: stray ‘\326’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\222’ in program
include/linux/compiler.h:312:3667: error: stray ‘\314’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\371’ in program
include/linux/compiler.h:312:3667: error: stray ‘\23’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\244’ in program
include/linux/compiler.h:312:3667: error: stray ‘\326’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\251’ in program

include/linux/compiler.h:312:3667: error: stray ‘#’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\244’ in program
include/linux/compiler.h:312:3667: error: stray ‘\320’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\360’ in program
include/linux/compiler.h:312:3667: error: stray ‘\215’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\306’ in program
include/linux/compiler.h:312:3667: error: stray ‘\344’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\232’ in program
include/linux/compiler.h:312:3667: error: stray ‘@’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\345’ in program
include/linux/compiler.h:312:3667: error: stray ‘\177’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\325’ in program
include/linux/compiler.h:312:3667: error: stray ‘\325’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\261’ in program
include/linux/compiler.h:312:3667: error: stray ‘\300’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\302’ in program
include/linux/compiler.h:312:3667: error: stray ‘\225’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\3’ in program
include/linux/compiler.h:312:3667: error: stray ‘\326’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\222’ in program
include/linux/compiler.h:312:3667: error: stray ‘\314’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\371’ in program
include/linux/compiler.h:312:3667: error: stray ‘\23’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\244’ in program
include/linux/compiler.h:312:3667: error: stray ‘\326’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\251’ in program
include/linux/compiler.h:312:3667: error: stray ‘#’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\244’ in program
include/linux/compiler.h:312:3667: error: stray ‘\320’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\360’ in program
include/linux/compiler.h:312:3667: error: stray ‘\215’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\306’ in program
include/linux/compiler.h:312:3667: error: stray ‘\344’ in program
include/linux/compiler-gcc.h:103:462: error: stray ‘\232’ in program
include/linux/compiler.h:312:3667: error: stray ‘@’ in programinclude/linux/compiler-gcc.h:103:462: error: stray ‘\345’ in program
...
...
etc

```

There is even much more error output but it looks like it is basically the same issue.

---

### Post by Ad@m on 2011-05-01
Which version of Ubuntu are you using? (Assuming 11.04)

Try this guide but modify where appropriate. Eg with kernel version 2.6.39-rc5

[http://linuxtweaking.blogspot.com/2011/04/how-to-recompile-your-ubuntu-1104.html](http://linuxtweaking.blogspot.com/2011/04/how-to-recompile-your-ubuntu-1104.html)

Substitute step 4 with this

```
[FONT=Arial]**4. Download and extract the vanilla 2.6.39-rc5 Kernel source**[/FONT]

wget http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.39-rc5.tar.gz

tar xfv linux-2.6.39-rc5.tar.gz
```

---

### Post by domcyrus on 2011-05-03
Thanks. Yes I am using 11.04. I've done another clean git checkout from torvalds tree which works flawlessly. 

One strange thing is that when doing a hexdump on the file which broke gcc e.g. include/linux/compiler.h:312:3661 there is no such ridiculous column 3661...

So it doesn't look like the kernel tree is somehow corrupted and therefore I suspect that make-kpkg may be broken in some way or some strange filesystem issue.

---

