---
title: "Which Ubuntu am I in?"
date: 2010-02-16
forum: General Help
---

### Post by dmfagan9 on 2010-02-16
Hi silly Q here- how do i determine if i am running 32 or 64 bit 8.10?? Thanks!!
Dylan

---

### Post by philinux on 2010-02-16
> **dmfagan9 said:**
> Hi silly Q here- how do i determine if i am running 32 or 64 bit 8.10?? Thanks!!
Dylan

Open a terminal and run this.

```
file /sbin/init

or 

uname -m

```

My 64 bit install gives this.
sbin/init: ELF **64-bit** LSB shared object, **x86-64**, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

---

### Post by audiomick on 2010-02-16
or this
[http://ubuntuforums.org/showpost.php?p=4988621&postcount=2](http://ubuntuforums.org/showpost.php?p=4988621&postcount=2)
or this
[http://ubuntuforums.org/showpost.php?p=8732062&postcount=8](http://ubuntuforums.org/showpost.php?p=8732062&postcount=8)

---

### Post by dmfagan9 on 2010-02-16
got it thanks!

---

### Post by fooey on 2010-02-16
del this post.

---

