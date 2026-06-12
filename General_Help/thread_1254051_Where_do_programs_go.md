---
title: "Where do programs go?"
date: 2009-08-30
forum: General Help
---

### Post by Clove7 on 2009-08-30
Okay, I downloaded a tarball to my /home/usr folder, extracted it there and compiled it there. Now, where can I go to find the compiled program? Can't seem to find it anywhere :confused:.

---

### Post by uylug on 2009-08-30
Right where you compiled it :p

After compiling, you can install it by doing

```
sudo make install
```

---

### Post by Clove7 on 2009-08-30
> **uylug said:**
> Right where you compiled it :p

After compiling, you can install it by doing

```
sudo make install
```
I did that. So the program is where I compiled it even after I installed it? :confused:

---

### Post by Clove7 on 2009-08-30
Oh, I see I found it. Where do programs go (where should they go) when you use apt-get install? I want to put the programs in their right spots :p.

---

### Post by uylug on 2009-08-30
If you "make install"ed it then it should be under your /usr/bin or /usr/sbin folder.

---

