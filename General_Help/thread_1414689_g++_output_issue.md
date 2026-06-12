---
title: "g++ output issue"
date: 2010-02-23
forum: General Help
---

### Post by gantis on 2010-02-23
If I try to test a c++ program, it seems to compile (doesn't show any errors, but will tell if there are any) but it doesn't show any output in the terminal, It's been working for weeks and I've never had an issue with this until now.  This is most likely not enough information, Please let me know what else you need to know and if I didn't it explain it well enough, say so. I am a student and this is a big deal right now.

Cheers

---

### Post by PhoHammer on 2010-02-23
> **gantis said:**
> If I try to test a c++ program, it seems to compile (doesn't show any errors, but will tell if there are any) but it doesn't show any output in the terminal, It's been working for weeks and I've never had an issue with this until now.  This is most likely not enough information, Please let me know what else you need to know and if I didn't it explain it well enough, say so. I am a student and this is a big deal right now.

Cheers

Output? g++ compiles your program, but does not run it. It (by default) compiles it to an "a.out" file, which can be ran by typing "./a.out" in the terminal after you compile with g++.

---

### Post by n0dix on 2010-02-23
You can try, 
g++ -o myprogram myprogram.cpp
then
./myprogram

---

### Post by gantis on 2010-02-23
Silly me, I guess I had a brain fart  ](*,). Thanks. It works with "./test". Don't know how I let that one slip.

Cheers

---

### Post by PhoHammer on 2010-02-23
> **gantis said:**
> Silly me, I guess I had a brain fart  ](*,). Thanks. It works with "./test". Don't know how I let that one slip.

Cheers

No problem, it happens to all of us!!

---

