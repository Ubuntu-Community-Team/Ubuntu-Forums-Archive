---
title: "does not compile C files"
date: 2010-02-13
forum: General Help
---

### Post by shulin v k satoskar on 2010-02-13
I have recently installed Ubuntu on my system.The terminal does not compile C files and gives errors related to including of header files .

---

### Post by GregBrannon on 2010-02-13
More detail would be helpful, like what terminal command did you try, what happened, etc.  But, lacking that, I'll suggest you try:

```
sudo apt-get install build-essential

```
if you haven't already.  If that doesn't solve your problems, come back with more info.

---

### Post by shulin v k satoskar on 2010-02-13
i used the command cc (filename).c

and it gave me all errors regarding the header files not included like header file stdio not included,printf does not have a prototype
do i need to include some files before compilation?

---

### Post by gmargo on 2010-02-13
If you have installed the **build-essential** package, then it must be a problem with your source code.  Have you tried The One True Program From Which All Others Are Descended?
```

$ cat world.c
#include <stdio.h>
main()
{
    printf("Hello, World\n");
}

$ make world
cc     world.c   -o world

$ ./world
Hello, World
```

---

