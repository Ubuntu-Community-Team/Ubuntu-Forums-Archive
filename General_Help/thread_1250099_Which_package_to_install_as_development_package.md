---
title: "Which package to install as development package?"
date: 2009-08-26
forum: General Help
---

### Post by cpthk on 2009-08-26
I am trying to install some libraries. I realized in linux, package for example libxxxxx has libxxxxx, libxxxxx-dev, libxxxxx-dbg. What's the difference between them?

If I just need the library and the headers for my developing program, do I install libxxxxx-dev? Do I still need to install libxxxxx and libxxxxx-dbg?

---

### Post by 3rdalbum on 2009-08-26
It's quite easy.

The regular "libxxxx" is required to run a program that depends on that library.

If you want to compile software that requires that library, then you need "libxxxx-dev". ("dev" is short for "development headers", probably)

If you're developing software that has that library, and you're getting problems that you think might be related to the library, you should install the -dbg version - it will provide your debugger with a lot more information. The extra information gathering does use a bit more processing power, which is why the -dbg versions aren't installed by default.

So, if you need the library and headers, install libxxxx and libxxxx-dev. Usually the -dev package pulls in the regular package too.

---

### Post by cpthk on 2009-08-26
so is the actual library in the libxxxxx or in -dev ? I see the description of the -dev, it sometimes says (includes, static library, manual pages). It seems contain library in -dev, not in main.

I saw it here: [http://packages.ubuntu.com/hardy/libcurl4-openssl-dev](http://packages.ubuntu.com/hardy/libcurl4-openssl-dev)

---

