---
title: "jvm"
date: 2012-04-19
forum: General Help
---

### Post by winzip on 2012-04-19
What is jvm maxpermsize option ?

---

### Post by solocommand on 2012-04-19
maxpermsize is the amount of heap space set aside that isn't garbage collected. This is in addition to whatever you set with -Xmx.

[http://www.oracle.com/technetwork/java/javase/tech/vmoptions-jsp-140102.html](http://www.oracle.com/technetwork/java/javase/tech/vmoptions-jsp-140102.html)

---

### Post by winzip on 2012-04-19
> **solocommand said:**
> maxpermsize is the amount of heap space set aside that isn't garbage collected. This is in addition to whatever you set with -Xmx.

[http://www.oracle.com/technetwork/java/javase/tech/vmoptions-jsp-140102.html](http://www.oracle.com/technetwork/java/javase/tech/vmoptions-jsp-140102.html)

What value should I set for a machine with 16 GB RAM.
How do you calculate this value ?

---

### Post by solocommand on 2012-04-19
Depends how much available memory you have. If you want to maximize performance, I would say probably 50% available for Xmx, and 25% for perm. You'd have to play around with these values to get the best mix from your machine though.

---

