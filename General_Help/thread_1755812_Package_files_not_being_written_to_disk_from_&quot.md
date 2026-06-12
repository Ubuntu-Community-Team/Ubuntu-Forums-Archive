---
title: "Package files not being written to disk from &quot;libxt-dev&quot;?"
date: 2011-05-11
forum: General Help
---

### Post by meridionaljet on 2011-05-11
Hi, I am compiling a program which is stopped by the fatal error that the file "Intrinsic.h" is not found. After searching Ubuntu packages, I discovered that the package "libxt-dev" contains this file. I installed this package, but this file (as well as the others it supposedly contains in the [file list]("http://packages.ubuntu.com/natty/amd64/libxt-dev/filelist")) never showed up on my hard disk. I reinstalled the package three times, restarted my computer, and even downloaded and compiled the source code, but the "locate" command still finds nothing:

```
levi@levi-laptop:/$ locate Intrinsic.h
levi@levi-laptop:/$ 
```

Any suggestions would be appreciated. I don't understand why the files contained in a package would not show up after installation of the package.

---

