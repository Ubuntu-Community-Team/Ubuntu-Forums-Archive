---
title: "How do I change swapiness on Ubuntu 9.10"
date: 2009-12-08
forum: General Help
---

### Post by lightningfox on 2009-12-08
Hello

I am using Ubuntu 9.10.

I read that increasing a desktop Linux system's swapiness (the amount of swap space it uses) makes it perform better, and that Andrew Morton, one of the major Linux kernel developers, has his desktop Linux system's swapiness set to 100.


I want to know how to change my Ubuntu 9.10's swapiness.


Please tell me how to do this.

---

### Post by jmszr on 2009-12-08
lightningfox,

About 2/3 of the way down this:[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) tells how to change the swappiness value. It does recommend a swappiness value of 10 for a desktop installation, but 100 you want, a 100 you can have.

---

### Post by mörgæs on 2009-12-08
How much memory does the machine have?

If you are concerned about performance, the best advice is to try to avoid swapping in general by giving the machine enough real memory.

---

