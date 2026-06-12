---
title: "How to Setup C"
date: 2011-09-09
forum: General Help
---

### Post by temecula on 2011-09-09
So my comp sci class this semester is systems programming in C in Unix/Linux environment and I Just recently installed Ubuntu and was wondering how to get C on it and compile via command line.  I was also going to use Sublime Text as a preferred text editor.  Also, I have never programmed on Linux before nor with C but I am familiar with Java and C++ so I was wondering if anyone knew of a tutorial with quick tips and stuff to help me get off the ground with a few basics.  Much obliged!

---

### Post by WorMzy on 2011-09-09
The GNU Compiler Collection (gcc) is already installed. All you need to do is write your .c (and .h, where applicable) files, then compile them with something like

```
gcc -o hello helloworld.c
```

There are plenty of tutorials out there which explain how to use gcc in more detail, but that should be enough to get you started with simple applications.

---

### Post by i.r.id10t on 2011-09-09
sudo apt-get install build-essential

---

