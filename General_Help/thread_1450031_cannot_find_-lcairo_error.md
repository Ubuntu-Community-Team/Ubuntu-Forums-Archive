---
title: "cannot find -lcairo error"
date: 2010-04-08
forum: General Help
---

### Post by jacky872 on 2010-04-08
Dear forum,

I'm trying to compile some C++ code, and I get this error while running make:

g++ -o TestMain -lm -lbz2 -lgd -DGD -lcairo -DCAIRO -I/usr/include/cairo -O4 -march=nocona TestMain.o Utils.o System.o Utility.o 
/usr/bin/ld: cannot find -lcairo
collect2: ld returned 1 exit status
make: *** [TestMain] Error 1

Any suggestions on how to resolve it?
Thanks.

---

### Post by gmargo on 2010-04-08
[SIZE=2]Do you have the **libcairo2** and [/SIZE][SIZE=2]**libcairo2-dev** packages installed? [/SIZE]

---

### Post by jacky872 on 2010-04-08
[SIZE=2] **libcairo2** was installed but not [/SIZE][SIZE=2]**libcairo2-dev**. It's fixed now, thanks.
[/SIZE]

---

