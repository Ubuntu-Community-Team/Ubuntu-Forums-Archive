---
title: "General question about 64-bit OS's"
date: 2010-04-29
forum: General Help
---

### Post by racie on 2010-04-29
Is there a point to installing a 64-bit OS on a dual core laptop if it only has 2GB of RAM?  It seems like there wouldn't be a difference in speed if I am correct.  This make me wonder why in the world the manufacturer decided to put 64-bit Vista on it.  :/

---

### Post by WinterRain on 2010-04-29
I've been using 64bit for quite some time now, and I can say that it seems a bit snappier and I can utilize all 6gb of RAM. I'll never go back to 32bit.

---

### Post by racie on 2010-04-29
Ahh, but see you have 6GB of RAM.  With 2GB I would think it wouldn't make much of a difference.

---

### Post by CharlesA on 2010-04-29
I try to use 64-bit if I can, even if I have less then 4GB of RAM (and a x64 CPU)

It is better at certain types of calculations, rendering and whatnot I believe. 

There's a thread on it somewheres.

---

### Post by carl4926 on 2010-04-29
> **racie said:**
> Is there a point to installing a 64-bit OS on a dual core laptop if it only has 2GB of RAM?  It seems like there wouldn't be a difference in speed if I am correct.  This make me wonder why in the world the manufacturer decided to put 64-bit Vista on it.  :/

If you wanted to put out a fire quickly, and you had the choice of two hose pipes.
One, With a 2cm diam
Another, with 4cm diam

which would you use?

And, Linux is years ahead in _64 bit OS, compared to Microsoft.

---

### Post by racie on 2010-04-29
> **CharlesA said:**
> I try to use 64-bit if I can, even if I have less then 4GB of RAM (and a x64 CPU)

It is better at certain types of calculations, rendering and whatnot I believe. 

There's a thread on it somewheres.

*ahem*  Would you happen to know where I could find said thread?  I'm curious. :P

---

### Post by CharlesA on 2010-04-29
> **racie said:**
> *ahem*  Would you happen to know where I could find said thread?  I'm curious. :P

I think it's in reoccurring discussions, but I cannot recall the exact title. Probably something to do with 64-bit.

---

### Post by srs5694 on 2010-04-29
I wrote an article years ago on the x86-64 (aka AMD64) architecture for Linux Magazine. You can read it [here](http://www.linux-mag.com/id/1699) (registration required). Although my article is old, the basic principles are still perfectly valid, even though the specific CPU models discussed are now quite archaic.

The brief answer to your question is that 64-bit per se offers very little over 32-bit aside from the ability to address more memory and more efficient 64-bit computations. In fact, 64-bit CPUs impose certain overheads, such as larger memory footprints for programs. That said, AMD's 64-bit extension to the x86 architecture (which is now used by both AMD and Intel) souped up the x86 CPU in ways that can provide a speed boost even on code that doesn't do a lot of 64-bit computations. The speed benefits vary from one program to another, but for CPU-intensive tasks, they're usually in the 5-30% range, with 10-15% being a good overall estimate of the improvement. This level of improvement may be noticeable, but it won't be what I'd call dramatic in most cases. (An exception might be something that's just struggling over some important threshold, like HD video playback on a marginal CPU -- the extra speed might be just enough to let the video play back without stuttering.)

The biggest drawback to an x86-64 CPU is software compatibility. A few programs don't compile properly in 64-bit mode, and some proprietary software isn't (and may never be) available in that form. Fortunately, most of these programs run fine in 32-bit mode, but there are exceptions. The one that gets mentioned most often is Adobe Flash, which is still only in alpha-test in 64-bit mode. This alpha reportedly works well for most people, but it's still got a few bugs. (Personally, I think Flash is about as appealing as a cockroach in my kitchen, but I'm in the minority on this.)

---

