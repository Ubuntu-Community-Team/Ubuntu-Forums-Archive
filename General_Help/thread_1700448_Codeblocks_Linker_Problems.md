---
title: "Codeblocks Linker Problems"
date: 2011-03-05
forum: General Help
---

### Post by flldom001 on 2011-03-05
Hi all,

I have written a program using pthreads. I have the #include<pthread.h> directive in the beginning of my file. and have specified pthreads library in the linker section of the compiler and debugger settings in codeblocks. However I get the following error on compilation:

-------------- Build: Debug in PracOne ---------------

Linking console executable: bin/Debug/PracOne
**/usr/bin/ld: cannot find -lpthreads**
collect2: ld returned 1 exit status
Process terminated with status 1 (0 minutes, 0 seconds)
1 errors, 0 warnings

I know the pthreads.h file is found in usr/include .

Please help.

Thanks.

---

### Post by flldom001 on 2011-03-05
Whoops the library is pthread.h not pthreads.h *blush*

---

