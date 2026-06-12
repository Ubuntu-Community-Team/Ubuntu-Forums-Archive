---
title: "Compiler error"
date: 2010-02-15
forum: General Help
---

### Post by Sidneyaks on 2010-02-15
Hello all. I've just tried to compile a program using the terminal and I keep getting the error

gcc: error trying to exec 'cc1plus': execvp: No such file or directory

I've been using the command

gcc -o quicksort quicksort2.cpp

Is there something I'm doing wrong, or is it a package I don't have? I've done a little bit of googling and found that I should install the g++ package, but when I try and use apt-get install it can't find the g++ package, nor can I find it in synaptic.

---

### Post by akashiraffee on 2010-02-15
Maybe it's already there!  Try:

**g++ -o quicksort quicksort2.cpp**

:p

ps. mergesort is more consistent, quacksort is for ducks

---

### Post by Sidneyaks on 2010-02-15
Nope :( Not there. I get this message

The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>

but when I try and get either of those packages, it says it can't find them.

And the quick sort is just for an algorithm class. We also have to do one for bubble sort as well as merge sort. :p

---

### Post by MinimalBin on 2010-02-15
The package is called [build-essential]("http://packages.ubuntu.com/karmic/build-essential") - install it and you should be fine :)

---

### Post by Sidneyaks on 2010-02-15
Thanks bin. :D 's all fixed up.

---

