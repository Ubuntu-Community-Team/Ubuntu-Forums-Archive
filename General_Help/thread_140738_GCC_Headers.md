---
title: "GCC Headers"
date: 2006-03-06
forum: General Help
---

### Post by Intell on 2006-03-06
Hi! Right now, I am trying to compile a C program that I wrote. But, the problem is GCC isn't installed properly. GCC works, but it reports errors that none of the header files are found. I've looked through the repositories, and I can't find a single thing. How can I install the headers? Here are the errors relating to the headers:
```

multiply.c:1:19: error: stdio.h: No such file or directory
multiply.c:2:20: error: stdlib.h: No such file or directory
multiply.c:3:20: error: string.h: No such file or directory

```

---

### Post by taurus on 2006-03-06
Try installing build-essential first and see if you still have problems with your c program...
```

sudo apt-get install build-essential

```

---

### Post by Intell on 2006-03-06
Ah, my C program works now. I'm always stuck at trivial problems. ;)

---

### Post by taurus on 2006-03-06
:mrgreen:

---

