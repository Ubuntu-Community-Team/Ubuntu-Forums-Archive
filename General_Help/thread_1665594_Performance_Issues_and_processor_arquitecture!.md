---
title: "Performance Issues and processor arquitecture!"
date: 2011-01-12
forum: General Help
---

### Post by galactus51 on 2011-01-12
Hello everybody, I will try to explain as best as possible to make my question!

Well, I'm compiling the kernel 2.6.34 or 2.6.36 for Ubuntu 10.10 64bits. I have a core i7 860 processor, accessing the menuconfig, right at processor family, if I check the family Core2/Xeon I have less performance from my kernel than if I use the option Pentium 4! No matter if I use the GCC version 4.4.4 or 4.5.1!
My question then is simple, Why I have a superior performance when using Pentium 4 architecture if the GCC documentation tells me I should use the Core2/Xeon for a better result?

I found this topic : [GCC] Compiling for a generic x86 architecture ([http://cboard.cprogramming.com/c-programming/127502-%5Bgcc%5D-compiling-generic-x86-architecture-2.html](http://cboard.cprogramming.com/c-programming/127502-%5Bgcc%5D-compiling-generic-x86-architecture-2.html))

Where cyberfish said:
> "mtune=... does NOT affect the instruction sets used, or machines the executable is run on.

For that (eg, enabling SSE), you'll need march=....

If you do march=core2 for example (on a new GCC), it will use all the instruction sets available to Core 2 CPUs. march=x also sets mtune=x. The executable won't run on older CPUs.

If you ONLY use mtune=core2, it will generate code that runs the best on a Core 2, but will still only use instructions available to all x86 CPUs (eg, no SSE), hence it will still run on old CPUs, just a little slower.

As a real world example, I think a few years ago some Linux distribution decides to use -march=pentium3 -mtune=pentium4, or something like that. That means, the code is guaranteed to run on a P3, but optimized for a P4, since they predict most people will be running for a P4.

If you don't use any flag, GCC will assume -march=i386 (lowest x86).

If you want GCC to use all instruction sets on your CPU, and optimize for your CPU (because, for example, the code will only be run on your machine), you can do -march=native (which also sets mtune=native). Only available in newer GCC (it was introduced in 4.3 or 4.4 I THINK).

-m32 and -m64 are only for generating 32-bit code on a 64-bit machine, or generating 64-bit code on a 32-bit machine, respectively. GCC defaults to 32-bit on 32-bit, and 64-bit on 64-bit."

So, the menuconfig processor family just change de mtune flag, and doesn't affect the march flag?

Can someone please give me an answer about this, please?

I am not a programmer, just an enthusiast but I can't find answers for it!

And if I put -march = core2 inside Kernel MakeFile, this could help?

---

