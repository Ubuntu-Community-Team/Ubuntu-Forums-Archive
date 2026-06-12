---
title: "Ubuntu System Monitor and Threading Display?"
date: 2011-02-17
forum: General Help
---

### Post by vsh3r on 2011-02-17
Hi,

I recently upgraded from an Intel i5 to a i7 Macbook Pro thinking that  it would be an 8 CPU system.  Much to my surprise after I purchased my  Macbook Pro i7 and started it up with Ubuntu 10.10 I see only 4 CPU's  running on the System Monitor.  

Intel has block diagrams of the i7 where it shows it has 8 cores/cpu's.

Two questions:  Is this false advertisement by Intel and secondly is  there any better way to display the 8 threads using the System Monitor  2.28.1?

Is this a bug with the Ubuntu System Monitor or just false advertisement by Intel or both?

[http://www.intel.com/products/processor/corei7/index.htm](http://www.intel.com/products/processor/corei7/index.htm)
[http://images.anandtech.com/reviews/cpu/intel/nehalemex/nehalemex.jpg](http://images.anandtech.com/reviews/cpu/intel/nehalemex/nehalemex.jpg)

):P

V$H.

---

### Post by Kirboosy on 2011-02-17
The i7 is only a quad core, but it hyperthreads so in some operating systems it appears as 8 cores. I have an AMD Phenom II and it appears as an 8 core system when in reality its only 4.

I also have a Dell Duo which appears as a quad core Atom processor and its only a dual core Atom processor.

Hyperthreading is the cause of all this nonsense. They claim hyperthreading gives you the power of having more cores but I think its a bunch of hype. Most OS don't use it fully. Dragonfly BSD is designed to handle hyperthreading really well but other than that I don't know if very many that utilize the technology

---

### Post by vsh3r on 2011-02-17
Is there anyway to update the System Monitor so that it shows performance in terms of each of the main core threads rather then the usage by CPU?

---

### Post by cascade9 on 2011-02-17
Yeah, the i7 is a 4core CPU (6 cores for some of the 'extreme editions'). 

Maybe hypertheading is disabled in the BIOS, or maybe there has been a minor mix-up and you've got sold a dualcore i5 mac pro. You could check lshw to see if its an i5 or i7.   

> **Caboose885 said:**
>  I have an AMD Phenom x2 and it appears as an 8 core system when in reality its only 4.

That shouldnt happen......AMD does not use hyperthreading. BTW, 'X2' is normally used for dualcores. I'd guess you mean Phenom II, which comes in X2 (dualcore) or X3 (tricore) or X4 (quadcore) or X6 (hexacore) variants.

---

### Post by Kirboosy on 2011-02-17
> **cascade9 said:**
> 
That shouldnt happen......AMD does not use hyperthreading. BTW, 'X2' is normally used for dualcores. I'd guess you mean Phenom II, which comes in X2 (dualcore) or X3 (tricore) or X4 (quadcore) or X6 (hexacore) variants.

Yes my mistake. My fingers got ahead of my brain. :rolleyes: None the less. It must have some sort of hyperthreading because I have '8 cores'...


As for the threading issue. I would contact Apple on it and see if they can explain it. Does it come up differently in OS X system monitor?

---

