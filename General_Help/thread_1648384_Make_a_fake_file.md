---
title: "Make a fake file"
date: 2010-12-18
forum: General Help
---

### Post by Verbeck on 2010-12-18
how could one create a file that takes up a lot of space on the drive?

---

### Post by noah++ on 2010-12-18
It can be done along these lines:


> To make a file of 100 random bytes:
  dd if=/dev/urandom of=/home/sam/myrandom bs=100 count=1(From [http://en.wikipedia.org/wiki/Dd_%28Unix%29]("http://en.wikipedia.org/wiki/Dd_%28Unix%29"))

---

### Post by Verbeck on 2010-12-18
thanx

---

