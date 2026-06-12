---
title: "Is it TRUE, Ubuntu gives more life to HDD"
date: 2009-12-07
forum: General Help
---

### Post by stealth_007 on 2009-12-07
Hi,
 
I heard one of my friend telling me that if we use Ubuntu HDD are going to be useful for years and it never fails.

My friend was telling that if we use Windows there are chances that the HDD will fail for sector errors caused by Windows File System and in Ubuntu, HDD never fails its because of different File System and Ubuntu has good File System. Is it True????

So our data is more safe & secured in Ubuntu rather than Windows???

---

### Post by stealth_007 on 2009-12-07
Please friends let me know whether it is true or not???

---

### Post by sdowney717 on 2009-12-07
windows scatters parts of files all over the drive. so the drive has to work harder picking up all the pieces. that is why they tell you to defrag windows.
linux does not do this, no defragging needed. so the drive does not have to seek all over the platter to pick up pieces of files.
so maybe it is true.
perhaps linux hdd drives run cooler than windows drives

---

### Post by stealth_007 on 2009-12-07
Thanks a lot....any more opinions Ubuntu friends...???

---

### Post by sikander3786 on 2009-12-07
> **stealth_007 said:**
> Hi,
 
I heard one of my friend telling me that if we use Ubuntu HDD are going to be useful for years and it never fails.

My friend was telling that if we use Windows there are chances that the HDD will fail for sector errors caused by Windows File System and in Ubuntu, HDD never fails its because of different File System and Ubuntu has good File System. Is it True????

So our data is more safe & secured in Ubuntu rather than Windows???

Your friend is absolutely correct. Linux's journaling file system is much safer and advanced than any other filesystem. Check the links below.

[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by foldingstock on 2009-12-07
Hard drives consist of moving parts, and because of this, they will all die eventually. Some are cheaply made and die sooner than others. 

Ubuntu can make your drive last longer for the reason sdowney717 posted. It could also make your drive die sooner for a number of reasons. YMMV. 

I've had hard drives on production servers last 10+ years and I have had other drives last as little as 2 months. In general, hard drives die from being used. The more you use a drive, the sooner it will die.

---

### Post by Slim Odds on 2009-12-07
> **stealth_007 said:**
> Please friends let me know whether it is true or not???

Did you really expect to get an answer in 30 minutes?

This is not instant messaging. Give it some time....

---

### Post by foldingstock on 2009-12-07
> **sikander3786 said:**
> Your friend is absolutely correct. Linux's journaling file system is much safer and advanced than any other filesystem. Check the links below.

[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

You are half-right. Journaling file systems are safer from power failures than non journaling file systems. They are slower, however, especially when dealing with several small files. The constant writes caused by journaling file systems will cause a hard drive to die sooner than a non journaling file system. 

This is not to say journaling file systems are bad, but since the op is concerned about hard drive life and not performance, they may not be the best option.

---

