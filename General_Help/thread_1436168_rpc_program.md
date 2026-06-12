---
title: "rpc program"
date: 2010-03-22
forum: General Help
---

### Post by prabhanjan2906 on 2010-03-22
I am trying to compile a simple remote procedure call program. i am getting an error 
/tmp/ccy0M5rT.o: In function `main':
rpchighlayer.c:(.text+0x5c): undefined reference to `rnusers'
collect2: ld returned 1 exit status

could any one pls help me to sort the error.
thanks in advance

```
#include <stdio.h>
#include<stdlib.h>
main(argc, argv)
int argc;
char **argv;
{
int num;if (argc != 2) {
fprintf(stderr, "usage: rnusers hostname\n");
exit(1);
}
if ((num = rnusers(argv[1])) < 0)
{fprintf(stderr, "error: rnusers\n");
exit(-1);
}
printf("%d users on %s\n", num, argv[1]);
exit(0);
}
```

---

### Post by soltanis on 2010-03-22
You are trying to compile a program for which a function (rnusers) is not defined.

Where did you get this program and what is it for? Chances are it's intended to be linked against some library that you either don't have on your system or you are not invoking the compiler with the correct options.

---

### Post by sugnanprabhu on 2010-12-10
Try installing portmap

---

