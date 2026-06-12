---
title: "Linking .so file..."
date: 2011-03-01
forum: General Help
---

### Post by sabarish_nr on 2011-03-01
[SIZE=3]hi,
[/SIZE][SIZE=4][SIZE=3]i have libmpc.so and libmpfr.so file in /usr/local/lib.. 
i need to softlink it to /usr/lib..
how do i do this..
pl give me d details..
thanks in advance...:popcorn:[/SIZE]
[/SIZE]

---

### Post by TeoBigusGeekus on 2011-03-01
```
cd /usr/lib
sudo ln -s /usr/local/libmpc.so /usr/local/libmpfr.so
```

---

### Post by sabarish_nr on 2011-03-02
> **TeoBigusGeekus said:**
> ```
cd /usr/lib
sudo ln -s /usr/local/libmpc.so /usr/local/libmpfr.so
```
thanks!!!

---

