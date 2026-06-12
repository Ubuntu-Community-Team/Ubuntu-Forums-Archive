---
title: "corrupted low memory"
date: 2011-03-25
forum: General Help
---

### Post by cody94 on 2011-03-25
I installed ubuntu 10.10 on my hp dv7 windows seven labtop. I installed ubuntu from within windows. It worked for a couple of months and then it came up with the message- corrupted low memory ffff880000006598. I have 4g of memory on my labtop and over 350gb of space free so this doesnt make sense. Please help

---

### Post by lloyd_b on 2011-03-26
First off, try running memtest86 (should be one of the options when you boot), just to verify that you're not dealing with an actual hardware issue (memory stick going bad).

Assuming that reports no problems, then you may have [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324894/").  The second to the last message in that thread provides a possible workaround to get the machine booting again.

Lloyd B.

---

### Post by 3rdalbum on 2011-03-26
> **cody94 said:**
> I installed ubuntu 10.10 on my hp dv7 windows seven labtop. I installed ubuntu from within windows. It worked for a couple of months and then it came up with the message- corrupted low memory ffff880000006598. I have 4g of memory on my labtop and over 350gb of space free so this doesnt make sense. Please help

It does make sense. "Low memory" is the name of a portion of your memory, not a description of how much memory is inside your computer. Therefore, "Corrupted low memory" is saying that the "low memory" portion of your RAM is corrupted.

---

