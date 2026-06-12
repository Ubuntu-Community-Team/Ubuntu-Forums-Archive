---
title: "possibly the easiest question on ubuntu forums!"
date: 2011-06-18
forum: General Help
---

### Post by xoron on 2011-06-18
so i installed ubuntu ages ago and i cant remember if its 32 bit or 64 bit. can someone tell me how to find out :D

thanks in advanced!

---

### Post by hiukkanen on 2011-06-18
```
uname -a 
```

If you don't see _64 anywhere but i686 or i386 its 32bit.

So if you see x86_64 or similar it is 64bit.

---

### Post by c-1000 on 2011-06-18
go to /var/cache/apt/archives. the .debs will either be i386 or amd64.

or open a terminal and run lshw.* -- edit: assuming you already know you have a 64 bit system. oops.*

---

