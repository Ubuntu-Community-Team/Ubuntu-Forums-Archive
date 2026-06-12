---
title: "Intel® Pentium® 4 Processor 631 showing 2 cores?"
date: 2009-12-01
forum: General Help
---

### Post by rmausser on 2009-12-01
Ok, so I installed ubuntu through Wubi, and I have a 

Intel® Pentium® 4 Processor 631 processor (3ghz)

To my surprise it installs ubuntu amd64.... my computer came with 32-bit Vista

So, apparently I have a 64-bit processor...score!

Well, under system monitor, it now says that I have 2 cores! (or two processors)

I looked up this processor, and it is definitely single cored. 

I dont care, because Ubuntu is running 5000X faster than vista... WOW its like I have a NEW computer! Less ram usage and my processor is being utilized like never before.

I just wanna know, why is Ubuntu using this computer with 2 cores if even the Intel website says it has one?

regardless this just proves how Ubuntu is FREAKING AWESOME!

---

### Post by Flying caveman on 2009-12-01
Yeah its using hyper-threading.  Ubuntu was way ahead of Windows with the 64 bit OS.

---

### Post by jbrown96 on 2009-12-01
Intel has a technology called Hyper-Threading. It makes one core look like two virtual cores. It can help the OS schedule tasks better when there are several applications running at the same time. If your computer still has the Intel sticker on it, you can tell because it will say "HT" on it.

The really surprising thing is that 64-bit installed. That's pretty crazy. Maybe it's acutally a Pentium D??? 

You can check if you are running 64-bit in a terminal (apps-->accessories-->terminal) with ```
uname -m
``` If it says x86_64, then it's 64-bit.

---

