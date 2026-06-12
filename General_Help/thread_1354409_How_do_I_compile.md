---
title: "How do I compile ?"
date: 2009-12-13
forum: General Help
---

### Post by raunchyrex on 2009-12-13
How do I compile C code in ubuntu? please help

---

### Post by lewisforlife on 2009-12-13
Is this a program that you downloaded, or a C program of yours that you are trying to compile.  If it is a program that you downloaded, normally:
```

./configure
make
make install
```

will do the trick, but it is always a good idea to read the README file that comes with it to look for special instructions.  If it is a program that you wrote in C, then use gcc, for instance, if you were compiling test.c, you would do it like this:

```
gcc test.c -o test
```

then you can execute test like this:

```
./test
```

---

### Post by FXEF on 2009-12-13
[http://ce.uml.edu/compile.htm]("http://ce.uml.edu/compile.htm")

Google is your friend.):P

---

### Post by john newbuntu on 2009-12-13
Make sure you have gcc.  sudo apt-get install gcc

---

### Post by raunchyrex on 2009-12-13
Thanks mate. I tries that guide and tried to compile a test.c program that I coded earlier

I get this error :(

> gcc: error trying to exec 'cc1plus': execvp: No such file or directory

Any help?

---

### Post by Queue29 on 2009-12-13
> **raunchyrex said:**
> Thanks mate. I tries that guide and tried to compile a test.c program that I coded earlier

I get this error :(



Any help?

```
sudo apt-get install g++
```

You must be writing C++ code, not C.

---

### Post by raunchyrex on 2009-12-14
lol.. my bad. Accidentally included C++ headers

---

