---
title: "slow copy from Ubuntu to XP shared folder"
date: 2010-06-09
forum: General Help
---

### Post by YigalB on 2010-06-09
lately, after shifting to 10.04,  when I copy files from the Ubuntu to my XP shared folders, it goes very very slow. i restarted the router and nothing changed.
I can see the folders, but the copy speed is still very slow.
Any idea why?

---

### Post by dcstar on 2010-06-10
> **YigalB said:**
> lately, after shifting to 10.04,  when I copy files from the Ubuntu to my XP shared folders, it goes very very slow. i restarted the router and nothing changed.
I can see the folders, but the copy speed is still very slow.
Any idea why?

Try setting a smaller MTU on the IPv4 network setting - ~1450 bytes.

---

### Post by YigalB on 2010-06-10
> **dcstar said:**
> Try setting a smaller MTU on the IPv4 network setting - ~1450 bytes.
Before you answered, I installed few utilities (but didnt use them) in order to debug the situation.
Somehow, now I can't see the network at all: I get: "Unable to mount location: failed to retrieve share list from server".

As for MTU: currently the number is 1500 in ET0' and 16436 in loop back.

---

