---
title: "what is the difference between dependency and pre-dependency?"
date: 2009-11-15
forum: General Help
---

### Post by chenxiaopang on 2009-11-15
For example, I found on my ubuntu 8.10
1) package **libc6** depends on **libgcc1** and **findutils**, 
2) **libgcc1** also depends on **libc6**
3) **findutils** pre-depends on **libc6**
My question: how the apt-get solve the dependency loop problem? How does the apt-get tool install the two packages(libc6 and libgcc1) which depends on each other? what's the difference between dependency and pre-dependency?

---

### Post by chenxiaopang on 2009-11-15
Anybody here?

---

### Post by mc4man on 2009-11-15
read here
[http://www.debian.org/doc/debian-policy/ch-relationships.html](http://www.debian.org/doc/debian-policy/ch-relationships.html)

---

