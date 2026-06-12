---
title: "New installation partitioning hard disc"
date: 2010-07-26
forum: General Help
---

### Post by David McGlade on 2010-07-26
I'm really taken with browsing Ubuntu 10.04 from memory stick, I can see me ditching Windows when I next buy a new computer but for now will use both until I am fluent in Ubuntu.
 
Please advise how much space to allow for the partition on my hard disc, so that I can use it as a dual boot system.  It is only 60mb (being a five year old Dell Inspiron) and there is 29mb free space.  
 
Many thanks,
 
Dave

---

### Post by prodigy_ on 2010-07-26
You should install Windows first and then Ubuntu because otherwise Windows bootloader (BCD) will overwrite Linux bootloader (Grub) and you'll have to take additional steps to restore Grub.

I also recommend you to read this these partitioning HOWTOs:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

And regarding your question, it depends on how much software (and what kind of software) you're going to install. ~10GB should be enough for root partition in most cases, I presume. I wouldn't recommend less than that however.

---

### Post by Goolie on 2010-07-26
> **David McGlade said:**
> I'm really taken with browsing Ubuntu 10.04 from memory stick, I can see me ditching Windows when I next buy a new computer but for now will use both until I am fluent in Ubuntu.
 
Please advise how much space to allow for the partition on my hard disc, so that I can use it as a dual boot system.  It is only 60mb (being a five year old Dell Inspiron) and there is 29mb free space.  
 
Many thanks,
 
Dave


Wait, I'm assuming you mean gigabytes. . .not the little little mb's.

But on my installation, I just booted into the CD and from their it guided me on partitioning the drive and made a little space for Windows and some on Ubuntu.  

Depends on what you plan on doing on both of them, you can keep Windows smaller or Ubuntu smaller.  Try cleaning up your Windows partition with something like CCleaner, and uninstalling useless apps and bloat.  Might save you some space and free up some more so the split decision won't be as hard.

---

