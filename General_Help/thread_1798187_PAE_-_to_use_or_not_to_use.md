---
title: "PAE - to use or not to use?"
date: 2011-07-06
forum: General Help
---

### Post by ClientAlive on 2011-07-06
I'm wondering if compiling a kernel to use physical address extension (PAE) would be beneficial or not if you don't actually have more than. 4 GB of memory. I have a machine with 1 GB of memory but the cpu is an amd that supports PAE. Since PAE uses more 36 instead of 32 bit adressing, I'm wondering if that doesn't just use up the memory I do have more quickly?

Also, and correct me if I'm wrong, I think there is actually 2 settings tied to this in compiling a kernel. There's enabling PAE or not and then there's selecting "off," "4 GB," or "64 GB" in another place.

Anything conclusive on what the best route to go is in a situation like mine?

Thanks in advance for any help.

Jake

---

### Post by An Sanct on 2011-07-06
I don't know about PAE, but if your processor supports 64bit, go for that one.

---

### Post by Grenage on 2011-07-06
PAE can be useful with machines that have 32-bit processors and lots of RAM.

If you have a 64-bit processor, use 64-bit.
If you have 4+ GB of RAM and a 32-bit processor, use 32-bit PAE.
If you have 4- GB of RAM and a 32-bit processor, use 32-bit.

---

### Post by nothingspecial on 2011-07-06
lol I remember your first ever post..... not that long ago.


.....and now you're compiling your own kernel =D>

With one gig of ram I don't think pae is necessary, but I don't really know what I'm talking about.

---

### Post by mcduck on 2011-07-06
Enabling PAE will actually hurt performance by creating extra work for the processor to do when it has to map the memory addresses, and also increases the RAM usage slightly.

You'd only want to enable it if you need more than 4GB of RAM and don't have 64-bit capable system. Using PAE doesn't bring any benefits other than the capability of addressing more memory.

---

### Post by dcstar on 2011-07-06
> **mcduck said:**
> Enabling PAE will actually hurt performance by creating extra work for the processor to do when it has to map the memory addresses, and also increases the RAM usage slightly.
.......

The whole point of PAE is separating more the 4GB of available RAM into 4GB segments that 32-bit systems can use.

If you don't have more than 4GB then PAE should be never used anyway, all you basically lose is the wasted space of the PAE code in the kernel.

---

### Post by ClientAlive on 2011-07-06
> **Grenage said:**
> PAE can be useful with machines that have 32-bit processors and lots of RAM.

If you have a 64-bit processor, use 64-bit.
If you have 4+ GB of RAM and a 32-bit processor, use 32-bit PAE.
If you have 4- GB of RAM and a 32-bit processor, use 32-bit.


I think I understand PAE a little better now. Thank you.


> **mcduck said:**
> Enabling PAE will actually hurt performance by creating extra work for the processor to do when it has to map the memory addresses, and also increases the RAM usage slightly.

You'd only want to enable it if you need more than 4GB of RAM and don't have 64-bit capable system. Using PAE doesn't bring any benefits other than the capability of addressing more memory.


That's the dynamic I was trying to get my head wrapped around. Circumstances dictate that I won't be putting more than 1 GB in er'; and, as you point out, it sounds like PAE would make for a performance decrease in 
my case. Thanks.

> **nothingspecial said:**
> lol I remember your first ever post..... not that long ago.


.....and now you're compiling your own kernel =D>

With one gig of ram I don't think pae is necessary, but I don't really know what I'm talking about.


lol. I revisit some of those old posts now and then; and get quite a chuckle out of em'. Now, sometimes, I visit other's threads and I see them freaking out and running all around like I did and I feel, well, real compassion for them (and a hint of amusement - to be honest).

I think I'm finding my way on this project I'm looking to do. I'm almost certain I'm gonna go with a stage 1 Gentoo install, possibly a recompile, then compile Xen or XCP (haven't decided which yet) on top of that. Then on to domU and some VM's. What I'd like to do is serve up VM's to my laptop (or any machine for that matter) over the Internet.
-------------------------/

Edit:

Well I guess I'm not as smart as I though . . .

> 
. . . the Gentoo Linux install process requires that all users compile their own Linux kernel.

Source: [http://en.wikipedia.org/wiki/Gentoo_Linux](http://en.wikipedia.org/wiki/Gentoo_Linux)


Funny thing, I read that before posting the above too. Just remembered it and went back there to re-read it.

---

