---
title: "Ubuntu Beowulf Cluster Questions"
date: 2011-12-01
forum: General Help
---

### Post by Antarctica32 on 2011-12-01
Ok, so I have very little money right now. I do however have around 12 or so Pentium 4s without HDDS. I really need a new computer thats fast and can handle some pretty heavy duty video editing (mostly 720p). One day it came to me that you don't need HDDs to make a cluster and then I thought why don't I just make a Beowulf cluster? So I was wandering:
Can I make an Ubuntu cluster?
Will ALL my programs take advantage of all the nodes, or will they just use the one?
Will this enable me to edit video better than 1 old P4?
How many P4s would it take to edit video? (should I just add the flops? would that be a reasonable way to determine how powerful the cluster is?)
Could someone point me in the right direction as to build this cluster?

all help of any kind is greatly appreciated. thanks in advance.

---

### Post by Antarctica32 on 2011-12-03
come on, any body? the info i found online is a little confusing and i just need somebody to answer those few questions before i even think of starting a project like this.

---

### Post by Antarctica32 on 2011-12-04
*bump

---

### Post by Rsjc741 on 2011-12-04
I don't see why not.

Though, video processing is usually done through the GPU, which in this case is probably the CPU if they're all intergrated graphics chipsets. However, if you have an old card that used an AGP or PCI video card, it could throw it off.

Video editing in itself isn't *that* resource intensive. I could edit 720P videos with relatively little lag/ no lag on a Gateway 420 GR w/ NVidia GT 240 Ti. That may of been a 2005-6.
It had a P4 @ 3.2 Ghz

I'd recommend getting a low end graphics card off Ebay or something for under 100, then find an old hard drive.

I think it would be a tonne more trouble networking roughly 12 computers together, then making them settle their differences, then somehow making an OS run off them.

Unless you've got a masters in computer engineering, plenty of time, and lots of dedication, then I wouldn't bother with it.
Besides, Ubuntu -barely-works well.
Heck, I've never had a fully function Ubuntu install over 3 machines, over 4 years.

---

