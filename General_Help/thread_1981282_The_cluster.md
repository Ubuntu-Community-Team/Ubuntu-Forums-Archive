---
title: "The cluster"
date: 2012-05-16
forum: General Help
---

### Post by AADAS on 2012-05-16
I want to make a super computer form many smaller laptops.I need soft for to make one big cluster computer.Can you help me?

---

### Post by cmont899 on 2012-05-16
Maybe openSSI, checkout openssi.org

---

### Post by Cheesemill on 2012-05-16
For what purpose? There are many different types of clusters depending on what sort of application you wish to run.

I hate doing this but have you looked here:
[http://en.wikipedia.org/wiki/Computer_cluster](http://en.wikipedia.org/wiki/Computer_cluster)

It has good descriptions about the different types of clusters as well as listing different software implementations.

---

### Post by AADAS on 2012-05-17
Well for now I want to make cluster for gaming.

---

### Post by AADAS on 2012-05-17
Better ideas?

---

### Post by Cheesemill on 2012-05-17
If you want to cluster together several laptops for the purposes of making a gaming rig then I'm afraid it's just not going to happen.

Computing Clusters run specialised software that dictates what sort of application you can run on them, and even then the applications have to be specially written for that type of cluster. You can't run normal software such as games on a cluster of several machines to try and get a boost in performance.

---

### Post by AADAS on 2012-05-17
So I can't separate the calculations between the machines? :-k

---

### Post by Cheesemill on 2012-05-17
Theoretically, yes.

But there is no way of transferring the information between the machines at a quick enough speed for it to work, and only specifically programmed applications will work on a cluster.

---

### Post by AADAS on 2012-05-17
So 2Gb/s is not enough?

---

### Post by Cheesemill on 2012-05-17
On an average gaming rig (using a PCI Express 16x GPU) the bandwidth between the CPU and the GPU is around 8GB/s (that's 64Gb/s).

But again it's nowhere near that simple.

Even modern games running on a modern gaming rig wont max out all of the cores available. You'll never see a game using 100% of the CPU available to it. This is because games aren't written with enough intelligence to use all of the processing cores.

Think of it like this, if a game can only use 2 cores on a 4 core chip then providing it with 100 available cores by using a cluster still isn't going to increase its speed at all. In fact it is likely to decrease the speed due to all of the additional overhead that is required by syncing all of the cores and transferring information betwwen them.

Honestly, what you are asking simply isn't possible.

---

