---
title: "which disk is which:?"
date: 2010-02-05
forum: General Help
---

### Post by Ceiber Boy on 2010-02-05
i downloaded and  burnt to disk two copy's of ubuntu 9.1 , one a 64-bit vershion and one a 32-bit version. but i've mixed up the disks and i can't tell which is which, how do i tell?

thanks

---

### Post by falconindy on 2010-02-05
Boot into one, and from a terminal, do:
```
uname -m
```
x86_64 = 64-bit
i686 = 32-bit

---

### Post by Mr Nemo on 2010-02-05
Load on disc and see what title comes up. AMD64 is 64 bit and i 386 is 32 bit. What does it tell you when you put one of the discs in your computer?

---

### Post by switch10 on 2010-02-05
boot one of the disks, open a terminal and type:

```
 uname -a 
```

near the end it gives the architecture.

i686 = 32 bit
amd64 = 64 bit

---

### Post by Ceiber Boy on 2010-02-05
They both say 

Ununtu 9.1 i386.

i'm really confused now.

---

### Post by switch10 on 2010-02-05
Then you downloaded 2 copies of the 32 bit version.

---

### Post by Ceiber Boy on 2010-02-05
my Desktop PC when i type 'uname -a' into the terminal gives

Linux chris-desktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

am i right in thinking that this is a 64-bit?


i think your right i must of downloaded two copy's of the 32-bit version

---

### Post by switch10 on 2010-02-05
yes your desktop is 64 bit.

---

### Post by Ceiber Boy on 2010-02-06
Thank you Everyone for your help

---

