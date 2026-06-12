---
title: "Do I need a swap partition if I have 4gb of ram installed?"
date: 2009-06-27
forum: General Help
---

### Post by asusx on 2009-06-27
Would I have a problem if I don't create any swap partition? 
Thanks

---

### Post by ~sHyLoCk~ on 2009-06-27
My swap stays at 0% always with 3Gb ram. But I guess it depends on what kind of app your running.

---

### Post by baizon on 2009-06-27
I recommend that article: [Should You Use Twice the Amount of Ram as Swap Space?]("http://www.cyberciti.biz/tips/linux-swap-space.html")
And to your question. I think you it will run without a swap, but i recommend to set some swap (if you have enough space). I have 2GB memory and 1GB swap space.

---

### Post by gldearman on 2009-06-27
Ubuntu does not *need* a swap partition to optimize memory.  It can use a swap file on the active filesystem, without needing a separate partition.

Also, I only have 1.5 GiB RAM, and my swap partition *never* gets used while the system is active.

However, you may want a swap partition for 2 reasons:

[LIST]
[*]Ubuntu cannot hibernate using a swap file.  It must have a swap partition.
[*]A swap partition can be shared with other Linux distros, whether installed on your system, or if you boot from a LiveCD.
[/LIST]

---

### Post by Hobgoblin on 2009-06-27
Like shylock says, it depends what you are doing.

You can always run the system monitor panel applet to keep an eye on memory usage.

For a normal desktop system 4GB should be plenty without swap.

---

### Post by ~sHyLoCk~ on 2009-06-27
> **baizon said:**
> I recommend that article: [Should You Use Twice the Amount of Ram as Swap Space?]("http://www.cyberciti.biz/tips/linux-swap-space.html")
And to your question. I think you it will run without a swap, but i recommend to set some swap (if you have enough space). I have 2GB memory and 1GB swap space.

Thanks for that link. Very helpful and proves my point of not using 2X swap space! I used just 1Gb, but it never used any!Ever!

---

### Post by asusx on 2009-06-27
Thanks guys...

---

### Post by chriskin on 2009-06-27
a user of these forums once wrote about the same question something like this:

swap is like the secondary parachute for the skydiver
chances are that you will never need it
but if you do, and do not have it, you're in serious trouble

so yes, considering i thought i did not need it using the same ram as you do, i have found some moments where swap gets used a lot

---

### Post by HavocXphere on 2009-06-27
You need it for suspend I think.

I'd suggest having at least a token amount of swap. I know some windows apps freak out if they can't find swap. Ubuntu apps will probably not.  But I don't see much point in finding out the hard way, especially when 2TB drives are available.

---

### Post by asusx on 2009-06-27
Well, is there a way I can make swap a directory in my root filesystem? I do not want to partition my drive, so is there a workaround to be able to suspend without a swap?

---

### Post by gldearman on 2009-06-27
> **asusx said:**
> Well, is there a way I can make swap a directory in my root filesystem? I do not want to partition my drive, so is there a workaround to be able to suspend without a swap?

You can *suspend* without a swap partition, you just can't *hibernate*.  The difference is that suspend has low power consumption, and hibernate consumes none (well, consumes the same as the computer would if powered off).

The instructions for creating a swap file are [here]("https://help.ubuntu.com/community/SwapFaq").  Let us know if you need more help than that page provides.

But I wouldn't be afraid of partitioning.  While there is some risk, it is easy, and generally very safe.  And GParted is a very safe way to do it -- it makes sure that you have previewed everything before it applies changes.

---

### Post by asusx on 2009-06-27
I'm not afraid of partitioning, but i have 4 primary partitions already so I can't resize any of the(takes too long) to make a swap.

---

### Post by gldearman on 2009-06-27
> **asusx said:**
> I'm not afraid of partitioning, but i have 4 primary partitions already so I can't resize any of the(takes too long) to make a swap.

Crap.  Do you have only one hard drive?  There's no rule that says the swap partition has to be on the same hard drive as the filesystem; mine isn't.

I'm guessing by your username that you have either a notebook or a netbook, so hibernate would be really useful, and putting a second hard drive in is not an option.

But if you want to hibernate, then, as far as I know, you must have a swap partition that is at least as large as your RAM.  I got that info from the link I gave you earlier.  Maybe it's wrong, or someone else knows a workaround.  Otherwise, you're going to have to repartition, as much as that sucks.

---

### Post by QIII on 2009-06-27
gldearman has the right answer on suspend/hibernate.

If you hibernate with less swap than you have RAM, you are asking for trouble.

Hibernate stores the RAM state in swap.  If you swap is smaller than the amount of RAM, the state information in your swap will be truncated or corrupt.

When you try to come out of hibernate, you will have an indeterminate state sent back to your RAM, and you will not be able to operate.

2x RAM is a bit silly.  Equal sized swap is needed for hibernate.  To be safe, follow the "10% extra" rule.

If you don't ever plan to use the hibernate feature, don't bother with a large swap.

---

