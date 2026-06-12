---
title: "Graphic Driver"
date: 2009-07-30
forum: General Help
---

### Post by pedrom169 on 2009-07-30
I am trying to download Graphic Driver from hardware drivers but when i hit activate it just sticks on 0%.

Anyone know how to fix it?

I am using 9.04

Cheers

---

### Post by overdrank on 2009-07-30
> **pedrom169 said:**
> I am trying to download Graphic Driver from hardware drivers but when i hit activate it just sticks on 0%.

Anyone know how to fix it?

I am using 9.04

Cheers

Hi, you may just need to update your system, you can use this command in the terminal located under applications, accessories.
```
sudo apt-get update && sudo apt-get upgrade
```
Or you may use update manager under system, administration.

---

### Post by pedrom169 on 2009-07-30
ran the command in terminal and tried to activate driver but till on 0%

ubuntu-bug jockey-common << says something about that

Cheers

---

### Post by pedrom169 on 2009-07-31
All fixed.

i ran sudo apt-get install build-essential linux-headers-`uname -r

and it fixed the problem

---

