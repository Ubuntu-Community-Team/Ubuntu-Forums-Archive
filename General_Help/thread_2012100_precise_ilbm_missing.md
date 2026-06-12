---
title: "precise ilbm missing"
date: 2012-06-28
forum: General Help
---

### Post by rlowrance on 2012-06-28
I just upgraded from 11.10 to 12.04.

My C program uses the sqrt function:

#include <math.h>
...

and compiles without error using gcc and clang.

However, in the link step, even though -lm is specified, the sqrt function is not found:

gcc -lm -lc knnHpSearch2.o Csv.o getline.o halt.o Log.o -o knnHpSearch2
knnHpSearch2.o: In function `distance':
/home/roy/build-linux-64/../src.git/knnHpSearch2.c:383: undefined reference to `sqrt'
knnHpSearch2.o: In function `main':
/home/roy/build-linux-64/../src.git/knnHpSearch2.c:582: undefined reference to `sqrt'
collect2: ld returned 1 exit status

The sqrt symbol seems to be in libm.a:

build-linux-64 $nm /usr/lib/x86_64-linux-gnu/libm.a | grep "sqrt"
nm: e_acos.o: no symbols
nm: e_rem_pio2.o: no symbols
0000000000000000 r sqrt_2.2530
nm: k_cos.o: no symbols
nm: k_sin.o: no symbols
e_sqrt.o:
0000000000000000 T __ieee754_sqrt
0000000000000000 T __sqrt_finite
nm: s_cos.o: no symbols
w_sqrt.o:
0000000000000000 T __sqrt
0000000000000000 W sqrt
                 U __csqrt
                 U __csqrt
<snip>

How can I fix this?

---

### Post by alexpage on 2012-09-11
Probable solution: [http://stackoverflow.com/questions/7824439/c-math-linker-problems-on-ubuntu-11-10](http://stackoverflow.com/questions/7824439/c-math-linker-problems-on-ubuntu-11-10)

---

