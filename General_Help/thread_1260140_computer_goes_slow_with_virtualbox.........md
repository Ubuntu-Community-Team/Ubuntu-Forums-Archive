---
title: "computer goes slow with virtualbox........"
date: 2009-09-07
forum: General Help
---

### Post by abhilashm86 on 2009-09-07
hi i'm using sun virtualbox, i want to constantly switch between two OS including MS, how much is efficient for virtual machine memory, i;ve given 1.3 GB, my total memory is 2.5 GB..........
is there any automatic efficient memory and processor utilization in ubuntu? it would be great if i find such a thing.......
you can see my sysmonitor.....

---

### Post by blueridgedog on 2009-09-07
Based on the image you posted, you system has maxed out the swap space.  A better command to post the output of would be:

```
free
```

If you run free prior to running virtualbox (but with your normal applications running) you will see what amount of memory you have that your system is not using.  I suspect you have allocated too much to your virtual machine.  I would use the minimum recommended for the OS you are using and bump it up until you have performance issues.  You may also want to increase the amount of swap space (either through another partition or through enlarging the one you have). 

When you start using swap, your system slows down, when you fill it up, it comes to a crawl.

I personally size my virtual machines so that I do not use swap.

---

### Post by P4man on 2009-09-07
> **abhilashm86 said:**
> hi i'm using sun virtualbox, i want to constantly switch between two OS including MS, how much is efficient for virtual machine memory, i;ve given 1.3 GB, my total memory is 2.5 GB..........

What else is eating up your ram?
edit: btw, you're running out of swap too.. !

> 
is there any automatic efficient memory and processor utilization in ubuntu? it would be great if i find such a thing.......
you can see my sysmonitor.....

You mean dynamically allocating ram to a VM ? Not possible im afraid. You cant dynamically install more ram in (native) windows either. The cpu load however, would be allocated automatically over your cores and apps/VMs, no need to do anything special for that.

---

### Post by abhilashm86 on 2009-09-07
> **P4man said:**
> What else is eating up your ram?
edit: btw, you're running out of swap too.. !


i was running some video tools, designer in MS and some webstuff in ubuntu...........
yea now i'l leave to kernel to decide on load of cpu!! ok thanks i got to know we can't alter memory dynamically........

---

### Post by Jazzy_Jeff on 2009-09-07
That is a very small amount of swap space allocated. My system has 5 gig of swap space allocated.

---

### Post by P4man on 2009-09-07
well, if nothing else, at least you should increase your swap space.. Not that it will speed things up considerably, but it avoids stuff no longer working :) 

Also Im not sure what you run in windows or what version, but perhaps try reducing the amount of ram you're giving it. Use a lean windows if possible (XP, perhaps even 2000, or TinyXP (40Mb Ram!) ).

---

