---
title: "gcc not generating output file for openCV"
date: 2011-08-31
forum: General Help
---

### Post by fallor_ergo_sum on 2011-08-31
hi

i just installed openCV 2.2. the installation went fine but when it came to executing codes i ran into problems. gcc is not generating any output file(a.out), even for a simple code.

here is how i compiled:
gcc -ggdb `pkg-config --cflags opencv` -o `basename $i .c` $i `pkg-config --libs opencv` first.c

gcc works fine for simple codes (no openCV libs)

can you people help me out.

thanks

---

