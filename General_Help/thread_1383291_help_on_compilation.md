---
title: "help on compilation"
date: 2010-01-17
forum: General Help
---

### Post by emari2 on 2010-01-17
I wanted to install a program with this lines
cd snort_inline-2.4.5a
./configure --with--mysql
make
checkintall
The second line works o.k. but on make
 the answer is that make do not exist or not found

---

### Post by akakingess on 2010-01-17
> **emari2 said:**
> I wanted to install a program with this lines
cd snort_inline-2.4.5a
./configure --with--mysql
make
checkintall
The second line works o.k. but on make
 the answer is that make do not exist or not found
You could try and make sure that it (or the correct version is installed ```
sudo aptitude install make
```this is just worth a shot, also, Ithink you may have misspelled checkinstall (missing the 's'). Don't know if either of these have anything to do with your problem, but it's a place to start.

---

### Post by john newbuntu on 2010-01-17
In general, when you are building/making/compiling code in C/C++, get the build-essential package and/or gcc at a minimum
```
sudo apt-get install build-essential 
```

---

### Post by SuperSonic4 on 2010-01-17
+1 for build-essential

---

