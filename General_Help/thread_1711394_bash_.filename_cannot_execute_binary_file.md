---
title: "bash: ./filename: cannot execute binary file"
date: 2011-03-21
forum: General Help
---

### Post by michiganitis on 2011-03-21
I have a file that was compiled on one machine. It works. On my home laptop, it says 'cannot execute binary file'. What's going on?

I compiled like this:


g++ -Wall -Werror -o filename depends.cpp file1.cpp file2.cpp file3.cpp file4.cpp file5.cpp

Did I compile wrong? Is it because of some difference from one machine to another?

Thanks!

---

### Post by Vaphell on 2011-03-21
maybe 32 vs 64bit issue?
run ```
uname -m
file yourbinaryfile
```
x86_64 is 64bit

---

### Post by michiganitis on 2011-03-21
> **Vaphell said:**
> maybe 32 vs 64bit issue?
run ```
uname -m
file yourbinaryfile
```
x86_64 is 64bit

oh that could be it. machine i'm at now is running ubuntu 64-bit. my laptop at home is 32-bit ubuntu. can you compile things in 64-bit to work with 32-bit os? is there a command or switch?

---

### Post by peely on 2011-03-21
if you can't get hold of a proper 64 bit compile, try installing the 32 bit libraries:

sudo apt-get install ia32-libs

Edit: Oh, just re-read and you are the other way round, no way to run 64 bit code on a 32 bit machine I'm afraid.

---

### Post by michiganitis on 2011-03-21
> **peely said:**
> if you can't get hold of a proper 64 bit compile, try installing the 32 bit libraries:

sudo apt-get install ia32-libs

Edit: Oh, just re-read and you are the other way round, no way to run 64 bit code on a 32 bit machine I'm afraid.

but can i recompile it? i thought there was a way to compile code on a 64-bit machine to run in 32-bit os?

---

### Post by peely on 2011-03-21
If you have the source code you can specify the -m32 command line switch into gcc.

---

### Post by cipherboy_loc on 2011-03-21
I think you can cross compile to 32 bit, but not sure there. Try googling how to cross compile...


Cipherboy

---

