---
title: "zRam"
date: 2012-09-12
forum: General Help
---

### Post by GeForce 9500GT on 2012-09-12
Did anyone heard of this tools: [zRam]("https://launchpad.net/~shnatsel/+archive/zram").
I found a description [here]("http://maketecheasier.com/four-ways-to-speed-up-ubuntu/2012/09/07"). Is it usefull?
 
> 
zRam is a tool that mimics the swap disk by creating a block in memory which functions as swap space. Since this &#8220;virtual swap&#8221; is created in RAM, it is much faster than the actual swap disk. If you have poor system configuration with low RAM, ZRAM will work really well. A must have tool for systems with less than 2 GB RAM.


---

### Post by Bucky Ball on 2012-09-12
*Thread moved to **General Help***

---

### Post by jerrrys on 2012-09-12
Bleachbit and preload are good ideas, but zram.  Swap is what is used when ram is low and sleep option is used.  Never used it, but doesn't sound like a good idea to me.

---

### Post by GeForce 9500GT on 2012-09-12
> **jerrrys said:**
> Bleachbit and preload are good ideas, but zram. Swap is what is used when ram is low and sleep option is used. Never used it, but doesn't sound like a good idea to me.
 
I'm really curious about this "fact":
 
*.....swap disk by creating a block in memory..........systems with less than 2 GB RAM.....*
 
If you're already low on memory, what's the use of creating a swap in the memory?? This must have the effect of leaving you with lesser memory, or am i wrong here????

---

### Post by LewisTM on 2012-09-12
I've experimented a bit with zram (package zram-config).

The concept is a but hard to grasp. When memory is low, it swaps some of it into a **compressed** ramdisk. Some say: this is stupid, it's taking away memory when you need it the most!

But if you think about it, it's just relocating the data elsewhere in RAM. So in effect you compress your ram, which gives you a slight edge in speed and stability when you're really low on memory. It's just way better to run on compressed memory than on virtual memory located on a slow hard drive.

With a fast hard drive or SSD, and with lots of RAM, it's rarely useful but it never hurts. Just like preload.

Cheers!

---

### Post by jerrrys on 2012-09-12
Think this is a better idea.

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by Bucky Ball on 2012-09-12
Hmm. Unless you are attempting to run on 128/256/512, I see no point. Open five apps and check how much RAM you're using then ponder whether this is worth pursuing. If you have a couple of Gb of RAM or more my guess is it's not.

---

