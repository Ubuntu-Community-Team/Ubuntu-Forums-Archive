---
title: "Only 3.4gb of 4gb showing up in Ubuntu 10.04 x64"
date: 2010-06-26
forum: General Help
---

### Post by blcArmadillo on 2010-06-26
I know, this question has been asked a million times, however, all the solutions I've found so far where people upgrading from a 32bit to 64bit version of Ubuntu. I'm currently running Ubuntu 10.04 x64 but only 3.4gb is showing up in the system monitor. Any ideas on how to fix this?

Motherboard: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813130269](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130269)
CPU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103843](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103843)
Memory: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820231277](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231277)

---

### Post by amauk on 2010-06-26
Onboard graphics (unless it has it's own memory bank) will siphon off memory from the main RAM

Also, the kernel has to sit somewhere
so that's half-a-dozen or so meg off, as well

---

### Post by blcArmadillo on 2010-06-26
Interesting. I would have expected the .6gb to be removed from my available RAM left count and not the total count. Another words I would have expected it to still report that there was 4gb installed and just start off at 3.4gb available.

---

### Post by dcstar on 2010-06-26
> **blcArmadillo said:**
> 
........
I'm currently running Ubuntu 10.04 x64 but only 3.4gb is showing up in the system monitor. Any ideas on how to fix this?

[LIST=1]
[*]Learn the difference between GiB and GB.
[/LIST]

---

### Post by hariprasad on 2010-08-07
I have the same problem, and i don't believe, that this is difference between GiB and GB, because:

1) The producer is doing the memory in GiB according my meaning in GiB, even if it is on pack written 4GB

2) Memtest issuing more than 4000000000, it really in GiB.

3) 4000000000/1024/1024/1024 = 3.725290298, not 3.4...

I must be something different. For example Integrated graphical card?

---

### Post by worksofcraft on 2010-08-07
Unused memory is a waste and so the system does it's best to use it for improved performance. Just because it isn't marked as free doesn't mean it can't be made available to applications if they should need it.

At this very moment I'm running Gimp to edit an image, Google Earth is open and so is Google Chrome (on this forum web page to be precise) I also have a little text file open in Gimp and a terminal window in which I run the free command:
```

$> free
             total       used       free     shared    buffers     cached
Mem:       4057524    1389200    2668324          0      58788     583272
-/+ buffers/cache:     747140    3310384
Swap:      4892664          0    4892664


```

as you can see I have oodles of unused memory left and nothing has needed to be swapped out, so meanwhile it makes perfect sense for some of that free memory to cache or buffers things instead of thrashing the hard disk ;)

---

### Post by CharlesA on 2010-08-07
It's probably taking memory for the onboard video.

Run **free -m** in a terminal and see what it says.

---

### Post by egalvan on 2010-08-07
> **blcArmadillo said:**
> Interesting. I would have expected the .6gb to be removed from my available RAM left count and not the total count. Another words I would have expected it to still report that there was 4gb **installed** and just start off at 3.4gb **available**.

The BIOS figures out and reports the amount of **installed ** RAM.
It then starts using some of this RAM for various code/data/page/init-vectors/pointers/bios needed to actually boot and run the machine.

What's left ( **available** ) is then reported to the OS as it boots.

Almost all Linux utilities report **available** RAM, 
not **installed** RAM.
And even the ones that DO report **installed** RAM usually take their count from the initial **available** RAM reported on boot.

For *nix, how much RAM is **installed** is nowhere near as important as how much RAM is **available**
As worksofcraft stated, *nix doesn't like unused RAM, so it tries to utilize it to speed up the system.


N.B. figuring out how much RAM is physically installed is not as easy as it may seem.
What with memory paging/translating, cache, etc. it's a daunting task to do correctly.

---

