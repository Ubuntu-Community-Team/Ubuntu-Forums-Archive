---
title: "Swappiness set to Zero, Still using swap...."
date: 2012-06-27
forum: General Help
---

### Post by nonedrinkwater on 2012-06-27
I've set swapiness to zero, but it still uses swap space when my machine reaches 500mb of ram, (i can see through conky that it uses it, and you can also tell by how slow it is)

i thought that it was my error so i checked if it's set to zero, and it is. 

strange... 

it worked great when i first set it to zero, now it's slow again. 

it's on an older machine, and I only have 1 gig of ram.... 

Any suggestions?

---

### Post by wildmanne39 on 2012-06-27
Hi, it is probably because it not using swap at all 1 gig of ram is not very much for ubuntu 12.04, and if you have to use swap it will slow down but if you need it and it is off then it will be real slow or non responsive.
Thanks

---

### Post by zombifier25 on 2012-06-27
Try setting it to 10.

When swappiness is zero, it means the system will avoid swapping as much as possible, not disabling swap completely.

---

### Post by nonedrinkwater on 2012-07-08
> **zombifier25 said:**
> Try setting it to 10.

When swappiness is zero, it means the system will avoid swapping as much as possible, not disabling swap completely.

brilliant! its fast now

---

