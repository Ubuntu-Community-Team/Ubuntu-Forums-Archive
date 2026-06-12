---
title: "c programming"
date: 2011-02-09
forum: General Help
---

### Post by piymon on 2011-02-09
i m a computer student and want to know if there is any application in ubuntu 10.10 in which i can write codes in c and c++ and run them on my laptop.
if so, what to do.

---

### Post by teaquack on 2011-02-09
I use vim and then compile it in terminal like ```
gcc -c -o myfile.o myfile.c
```

---

### Post by slooksterpsv on 2011-02-09
> **piymon said:**
> i m a computer student and want to know if there is any application in ubuntu 10.10 in which i can write codes in c and c++ and run them on my laptop.
if so, what to do.

Lots.

I personally like Eclipse the the CDT Plugin, so that I can write C++ code. Eclipse is in the Ubuntu Software Center, along with gcc, g++ (for C and C++ respectively), or you can do build-essential, which gets you all the essentials for compiling software.

You can use gedit and compile with the terminal via:
gcc -o myprog main.c
g++ -o myprog main.cpp

Another good editor is Code::Blocks, haven't used that one much, but others say its amazing.

---

### Post by Hrexen on 2011-02-09
You can use CDTs for example Eclipse or NetBeans. There is a lot of them.

---

### Post by piymon on 2011-02-09
thanks for that guys. i will install eclipse and get back to u for further help if needed on this thread

---

### Post by GregBrannon on 2011-02-09
Check the stickies in the Programming Talk sub-forum for more help getting started with programming.  There have also been many threads discussing IDEs.

---

