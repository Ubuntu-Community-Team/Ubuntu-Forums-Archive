---
title: "cpp-3.4 is set to manually installed ??"
date: 2009-08-25
forum: General Help
---

### Post by cpthk on 2009-08-25
Hi:

ubuntu has by default gcc 4. gcc 4 is in experimental status, and I have a library that really need gcc 3 for now. I do:
```

apt-get install gcc-3.4

```
Later I saw this message say cpp-3.4 is set to manually installed. It seems like it didn't get to install. I tried to compile my code, it says "language c++ not recognized"

How do I install cpp-3.4?

---

### Post by credobyte on 2009-08-26
```
sudo apt-get install g++-3.4

```I'm at work - cannot verify.

Btw, what version build-essential contains ?

---

### Post by cpthk on 2009-08-26
I think you are right, but seems ubuntu completely discontinue g++-3.4.

So what's the difference between all these packages?
gcc-3.4
cpp-3.4
g++-3.4

---

