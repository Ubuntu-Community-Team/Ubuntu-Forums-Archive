---
title: "Transfer momory from shared in duel boot?"
date: 2010-06-27
forum: General Help
---

### Post by cheekymonky2010 on 2010-06-27
Could anyone please tell me how to transfer memory from the shared location to ubuntu default memory?  I have windows 7 and Ubuntu 10 on duel boot and don,t really use Windows and would also like to take a few Gigs from there if I knew how?

---

### Post by slooksterpsv on 2010-06-27
You can resize the partitions with gparted - install it it from Ubuntu Software Center, but the problem is lets say your partitions look like this:

[WINDOWS___________][LINUX______]

If you resize Windows here's how the partitions will look:

[WINDOWS________][___][LINUX_____]

Where the [___] is an empty partition. Now how to get that to add to Linux, I don't know. But gparted is a start, least you could do is grab some GB, make those GB their own partition and be like your downloads or that.

---

### Post by cheekymonky2010 on 2010-06-27
Thank you very much I will do that

---

### Post by Barafu Albino Cheetah on 2010-06-27
You should download Gparted LiveCD from thier web-cite and write it to disk. Then boot from it. Generally, GParted is easy to use, but you should know that it can be performing its operations for tens of hours, and you may not turn off you pc during that or you eill loose your data.

---

