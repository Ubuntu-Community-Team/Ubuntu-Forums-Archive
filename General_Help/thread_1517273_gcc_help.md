---
title: "gcc help"
date: 2010-06-24
forum: General Help
---

### Post by COKEDUDE on 2010-06-24
The man pages of gcc say it is both a C and C++ compiler. So I don't understand why I can't compile my C++ program with gcc. Is there a specific command that you need to make it work? Or is there another problem? C programs compile just fine.

---

### Post by amauk on 2010-06-24
Use g++
that's the GNU C++ compiler

```
g++ -o myprog myprog.cpp
```

The naming used by GNU is a bit ambiguous, but

GCC (the software collection) = Gnu Compiler Collection

GCC (the program) = Gnu C Compiler

G++ = Gnu C++ Compiler

---

### Post by COKEDUDE on 2010-06-24
Whats the first myprog for? Would that be something like the a.out in c with gcc? I know the myprog.cpp is the file. Could you also use the -Wall option to show all the warnings? I like seeing all the warnings.

---

### Post by amauk on 2010-06-24
> **COKEDUDE said:**
> Whats the first myprog for? Would that be something like the a.out in c with gcc? I know the myprog.cpp is the file. Could you also use the -Wall option to show all the warnings? I like seeing all the warnings.

The first myprog is the name of the binary file
the -o specifies the 'output file'
compile 'myprog.cpp' to an executable called 'myprog'

Yes, you can use -wall (and any other options you want)

---

### Post by COKEDUDE on 2010-06-26
Cool it worked great :).

---

