---
title: "Gnu Make Install Error"
date: 2012-06-08
forum: General Help
---

### Post by marty331 on 2012-06-08
trying to make Gnu make and getting the following error. Ubuntu 12.04 64 bit. Any help?



make-3.81$ make
/bin/bash: -c: line 0: syntax error near unexpected token `;;'
/bin/bash: -c: line 0: `if test ! -f config.h; then  rm -f stamp-h1;  make stam-h1;;  else :; fi'
make: *** [config.h] Error 1

---

### Post by dino99 on 2012-06-08
review the syntax, as shown in the output (line 0)

---

### Post by marty331 on 2012-06-08
I don't know where line 0 is coming from, any idea?

What I had done prior to the error was:
./configure
make  --- this is where I got the error.

---

