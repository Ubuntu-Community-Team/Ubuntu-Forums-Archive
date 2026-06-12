---
title: "32-bit and 64-bit java switch"
date: 2010-03-03
forum: General Help
---

### Post by xingerguan on 2010-03-03
I'm using a 64-bit machine, and naturally everything is based on the 64-bit. However I need to get the Juniper Network Connection running, which only works for 32-bit java. 
How should I download the 32-bit java so that it won't interfere with other application using 64-bit java, and set the PATH so that the 32-bit java is used when I use Juniper Network.

---

### Post by GregBrannon on 2010-03-03
The Java Virtual Machine (VM) on your computer is either 32- or 64-bit.  Based on your post, I'm assuming you have the 64-bit VM.  If you're Juniper Network in Java code has already been compiled to Java bytecode, then that bytecode should run properly on a 32-bit or a 64-bit VM.

You shouldn't have to do anything differently.

---

### Post by berezhinskiy on 2011-06-26
```
sudo apt-get install ia32-sun-java6-bin
```

---

