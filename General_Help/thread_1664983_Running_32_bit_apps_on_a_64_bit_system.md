---
title: "Running 32 bit apps on a 64 bit system"
date: 2011-01-11
forum: General Help
---

### Post by BigYellowDog on 2011-01-11
I have a 32 bit program that I use to stream music to a shoutcast server.  The problem is it will not execute on a 64 bit Ubuntu system, I was previously able to run it on a 64 bit Fedora system.  It also runs fine 32 bit Ubuntu, no surprise.  

> 
[rob] ~/sc_trans_040 $ ./sc_trans_linux 
bash: ./sc_trans_linux: No such file or directory
[rob] ~/sc_trans_040 $ 

[rob] ~/sc_trans_040 $ file ./sc_trans_linux 
./sc_trans_linux: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped
[rob] ~/sc_trans_040 $ 


---

### Post by BicyclerBoy on 2011-01-11
My experience of 32 bit/64 bit is with nvidia gl libs & wine.

To run 32 bit aps you need the appropriate 32 bit  dynamic libraries installed.

i.e. for openGL stuff I have had 32 & 64 bit libraries & headers etc..

---

### Post by oldos2er on 2011-01-12
```
sudo apt-get install ia32-libs
```

---

### Post by BigYellowDog on 2011-01-12
> **oldos2er said:**
> ```
sudo apt-get install ia32-libs
```

Thanks :P that worked.

---

### Post by oldos2er on 2011-01-12
You're welcome.

---

