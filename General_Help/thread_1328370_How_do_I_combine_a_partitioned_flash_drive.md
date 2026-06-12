---
title: "How do I combine a partitioned flash drive?"
date: 2009-11-16
forum: General Help
---

### Post by RonB123123 on 2009-11-16
I have a 2 GB flash stick and I have 1 partition of 1.995 GB and another partition of .005 GB. How would I go about combining my partitions to make a full flash stick?

If you're wondering, I installed puppy linux a long time ago and never got the chance of fixing the partitions. 

Thank you

---

### Post by hwttdz on 2009-11-16
I'd fire up gparted and see what you can get done in there. Sidenote: gparted requires super powers, so gksudo gparted.

---

### Post by Zoot7 on 2009-11-16
Use gparted.

Delete the partition you don't want and grow the one you do want into the empty space.

---

### Post by RonB123123 on 2009-11-25
I started GParted and it recognized each partition of my flash stick as a separate device. So partition 1 is /dev/sdb and partition 2 is /dev/sdc. I can't find a way to combine them. Is there a way to do this through the terminal?

---

