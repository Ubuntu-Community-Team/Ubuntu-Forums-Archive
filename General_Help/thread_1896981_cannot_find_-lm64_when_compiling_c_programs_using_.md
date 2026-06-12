---
title: "cannot find -lm64 when compiling c programs using gcc"
date: 2011-12-18
forum: General Help
---

### Post by login failed on 2011-12-18
Hi,

I was compiling small C programs using 'gcc -Wall -g -lm64 -o foo bar.c' and I got the following error message:

```
/usr/bin/ld: cannot find -lm64
collect2: ld returned 1 exit status
```

The 11.10 AMD64 system have gcc and gcc-multilib installed. Does someone have an idea of fixing the issue?

Thank you.

---

### Post by hwttdz on 2011-12-20
Try

```
gcc -Wall -g -o foo bar.c -lm
```

---

