---
title: "Cache problem"
date: 2009-08-24
forum: General Help
---

### Post by sfantus1 on 2009-08-24
hello guya i have a slight problem and i don`t know what`s wrong

I just reinstalled ubuntu on my machine and my memory usage is at maximum :( 51% in cache and 46% in programs i have 1gb or ram and  i didn`t have this problem last time could anione tell me what this means 51% in cache

thanks:confused:

---

### Post by sfantus1 on 2009-08-25
please some help

---

### Post by kerry_s on 2009-08-25
every program you open is cached for faster access the next time.

---

### Post by sfantus1 on 2009-08-25
and this is normal?
Can i see wich program uses the most ?

---

### Post by bapoumba on 2009-08-25
Some application reserve memory for their own use (but only use it when needed). Linux memory handling is quite different from windows. If you do not see any sluggishness in your system, all is okay :)
[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

Edit: I was too slow, looking for that link I had not bookmarked ^^

---

### Post by nikhilk on 2009-08-25
> **sfantus1 said:**
> and this is normal?
Can i see wich program uses the most ?

With default settings, yes this is normal. Most of the unused RAM is used as cache by the kernel. It does not belong to any one process. Kernel uses it as disk cache to minimize disk I/O which very slow compared to reading from RAM.

---

### Post by sfantus1 on 2009-08-25
ok guys thank you my machine isn`t slow so if you say this is normal then great

thanks again

---

