---
title: "Chronic DVD-writing problems"
date: 2009-08-10
forum: General Help
---

### Post by DGeeez on 2009-08-10
How could one be so unlucky with the most popular DVD-writing software for Ubuntu, or is it something other than luck? Could it be crappy integrated ATI hardware? Would buying a video card fix a problem like this, or do I need a whole different Linux-freindly PC? Here are the specs:

d:	
display
description: 	VGA compatible controller
product: 	RS690 [Radeon X1200 Series]
vendor: 	ATI Technologies Inc
physical id: 	
5
bus info: 	
pci@0000:01:05.0
version: 	00
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi bus_master cap_list
configuration:	
latency	=	64

While most programs will write a video file to my DVDs, they all have some sort of problem with writing them as DVD disks which are readable by non PC or laptop driven units. Gnomebaker may have more problems, but I tried adding multiple small files (way under the capacity limt), and every time I tried to add the second item, the whole program suddenly shut down. K3b would write to my media, but a DVD production project always ends with an error, it was something about being unable to determine volume size (again I was not overloading capacity). Brasero consistently choked, sputtered, and hung with a dark, blank, and ugly window until I put it out of it's misery with the force-quit bullet, and the fatal shot came after I installed the dvd+rw-tools - somehow this Nautilus add-on could not co-exist with Brasero (not that I'll probably miss it)! I keep installing different programs, but they either can't write a production DVD on my computer, or they don't have that feature at all (like dvd+rw-tools - somebody should explain why an add-on which does not offer full-feartured DVD production can't be produced without displacing one which is). 

This is really driving me crazy, so please help if you can. Nothing else on my machine, video or otherwise seems affected, just the the full DVD production, which I really need to do a lot of soon. I can't decide if it's even worth trying to find another program, there must be a system variable which they are all choking on, but what could it be, and can it be fixed without changing the hardware?

Thanks.

---

### Post by arky on 2009-08-10
Try testing with DVD+-RW/R tools package and file a bug against the DVD authoring tool when you are stuck. 

Hint: ubuntu-bug <program-name>


Also don't think graphic card would have anything to do with this.

---

### Post by stinger30au on 2009-08-10
im lost as to why you think the video card is somehow related to the dvd errors

do you have another pc you can rob the dvd drive from and test it with?

borrow/pinch one from a mate's place?

buy a new dvd drive.
they practically give them away in the bottom of weet-bix packets now days anyhow as the prize in the bottom of the box

---

