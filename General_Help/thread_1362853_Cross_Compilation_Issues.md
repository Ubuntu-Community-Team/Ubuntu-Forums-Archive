---
title: "Cross Compilation Issues"
date: 2009-12-23
forum: General Help
---

### Post by kartiknatarajan on 2009-12-23
Hi, 

I am posting another issue regarding cross compilation. While cross compiling Mono for XScale ARM I am getting the following error,

```
/usr/local/lecs/stargate-linux/lib/gcc-lib/arm-linux/3.2/../../../../arm-linux/bin/ld: cannot find -lgthread-2.0
```

Can anyone suggest a solution or a work around. Thanks a lot.

---

### Post by kartiknatarajan on 2009-12-23
Bump!

---

### Post by kartiknatarajan on 2009-12-23
Can anyone help me with this?

---

### Post by john newbuntu on 2009-12-24
gthread library appears to be a part of libglib2.0-dev package.  I haven't used it myself.  But try installing/re-installing this library from synaptic and see if it helps.

---

