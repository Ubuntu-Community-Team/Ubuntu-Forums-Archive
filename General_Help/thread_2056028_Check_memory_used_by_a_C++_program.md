---
title: "Check memory used by a C++ program"
date: 2012-09-10
forum: General Help
---

### Post by layers on 2012-09-10
I have a C++ algorithm that manipulates a bunch of matrices in C++, which I know can run on an Altera DE1 board (which has 8MB SDRAM, 512K SRAM, and 4MB Flash). I want to put the program on an Arduino Uno (2KB SDRAM, 1KB EEPROM, 32KB flash), but I am not sure if the Uno can take it and run it (scared it will keep running out of memory).

What is the best way to check? Should I run the program on my computer and somehow follow the average memory it uses?

---

### Post by mevun on 2012-09-10
I don't think the test on your regular computer (Ubuntu linux?) will be very helpful.  Arduino uses its own "operating system", so it may not be using the same standard library as your Linux if you do dynamic memory allocation.  Plus, the fact that your CPUs are probably different might have an effect.

If you're doing static memory allocation, you can probably guess its size by just analyzing the size of matrices.  Sometimes there are tools like "nm" that can tell you the statically allocated memory after the linker is finished.  At least, I think it can do that for ELF format.  I don't know what file format Arduino linked output is, but they may have a similar tool.

---

### Post by layers on 2012-09-10
So none of the IDE's don't have this feature? At least to give some number, just so I know if I'm way over it.

---

### Post by Vaphell on 2012-09-10
ask in programming talk forum
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by mevun on 2012-09-10
Or maybe ask in an Arduino forum.  I only know a little bit about Arduino based on various presentations/demos I've seen.

---

