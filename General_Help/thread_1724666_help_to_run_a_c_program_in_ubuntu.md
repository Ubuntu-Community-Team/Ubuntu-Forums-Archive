---
title: "help to run a c program in ubuntu"
date: 2011-04-08
forum: General Help
---

### Post by sharathchav on 2011-04-08
hi,
i am new to ubuntu...with the help of internet and this forum I was able to compile a c program written in a gedit..
the program goes like this
#include <stdio.h>

main()
{
 printf("hell0");
}

then i compiled it using this: sudo gcc 1.c
and then i get a *.out file...
my question is how can i see the result of my program...please help me...i have spent lot of time trying to figure out wht went wrong....

---

### Post by seawolf167 on 2011-04-08
The a.out is your program, if you open a terminal (Applications -> Accessories -> Terminal), then browse to the directory containing your a.out file

```
cd /path/to/directory
```

then run your program (contained in that directory)

```
./a.out
```

---

