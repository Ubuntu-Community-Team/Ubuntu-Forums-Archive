---
title: "gcc cannot find libraries"
date: 2006-02-08
forum: General Help
---

### Post by cerenbudak on 2006-02-08
hi
I am new to Ubuntu and Linux, my problem is although I have downloaded all the gcc files in Package Manager still I don't have the libraries and my C files do not compile giving errors like:
bilsort.c:1:19: error: stdio.h: No such file or directory
bilsort.c:2:20: error: stdlib.h: No such file or directory


can anybody help me?

---

### Post by taurus on 2006-02-08
Try

sudo apt-get install build-essential

---

### Post by cerenbudak on 2006-02-08
thanks : )

---

