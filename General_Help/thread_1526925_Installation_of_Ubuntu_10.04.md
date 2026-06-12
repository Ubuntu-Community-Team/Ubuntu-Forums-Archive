---
title: "Installation of Ubuntu 10.04"
date: 2010-07-08
forum: General Help
---

### Post by virsto on 2010-07-08
I very recently used Wubi to install Ubuntu 10.04 LTS and then I ran
 
uname -a
 
which gave
 
**Ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux**
 
And now for perhaps a silly question --- Is this really a 64-bit OS?:o

---

### Post by marshmallow1304 on 2010-07-08
Yes.

---

### Post by virsto on 2010-07-08
Thanks Marshmellow.
Is there any system test that I can peform that proves that it is a 64-bit machine?

---

### Post by marshmallow1304 on 2010-07-08
```
uname -m
```
tells you the OS architecture.

```
sudo lshw -c cpu | grep width
```
tells you about the CPU.

---

