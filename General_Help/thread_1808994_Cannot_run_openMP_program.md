---
title: "Cannot run openMP program"
date: 2011-07-21
forum: General Help
---

### Post by ausairman on 2011-07-21
I have a C++ program that I tried to compile with some parallel processing using openMP. However, when I compile and run the program in Ubuntu I get the following error:

```
Operation not permitted /home/uqaschwa/Train: error while loading shared libraries: libgomp.so.1: cannot open shared object file: No such file or directory
```

I am compiling my program using the GCC compiler in Code::blocks with the -fopenmp flag and -lgomp linker options. In the repository I have version 4.5.2ubuntu4 of libgomp1 installed.

---

