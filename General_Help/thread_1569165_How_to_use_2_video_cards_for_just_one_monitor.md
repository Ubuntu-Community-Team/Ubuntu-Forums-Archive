---
title: "How to use 2 video cards for just one monitor"
date: 2010-09-06
forum: General Help
---

### Post by crazyfuturamanoob on 2010-09-06
I have 2 video cards installed, and I only have one 22" monitor (1680x1050 pixels).
[list][*]ATI Radeon HD 4290
[*]Nvidia 7300 GT Silent[/list]
How can I make the both video cards render OpenGL stuff at the same time? Is it even possible?

And which GPU is faster? ATI Radeon HD 4290?

---

### Post by Mark Phelps on 2010-09-06
> **crazyfuturamanoob said:**
> How can I make the both video cards render OpenGL stuff at the same time? Is it even possible?

Having two cards is not the problem -- the problem is that your monitor will accept input from only one source at a time.  So, while it may have two input jacks, and you could hook each card up to one of the jacks, it will only use one jack at a time.

You should be able to switch back and forth between input sources for your monitor, but that's still only using one source at a time.

---

### Post by HPD2 on 2010-09-07
Sounds like your trying to run an SLI or Crossfire setup. I don't think it can be done with two different cards. You would need two ATI or Nvidia cards to Crossfire or SLI the GPU's.

---

### Post by crazyfuturamanoob on 2010-09-07
If I get another NVidia 7300 GT and use SLI, is it faster than using just the Radeon HD 4290?

---

### Post by cascade9 on 2010-09-07
Unless I'm mistaken, HD4290 is onboard video only. Its an ATI chipset so you wont be able to run SLI (ATI is crossfire only). 

Even if you could run SLI, 2 7300GTs are still going to be very slow, even on games that have good SLI support. On games with poor/nonexistant SLI support, its going to be no faster than a single card. 

You'd be better of saving your money and buying a decent card.

---

### Post by linux-hack on 2010-09-07
How can you activate the gpu on linux ?? does someone know that ?

---

### Post by Mark Phelps on 2010-09-07
> **boogy9 said:**
> How can you activate the gpu on linux ?? does someone know that ?

What has this to do with the original question of using 2 video cards?

Anything?

IF not, please do NOT hijack this thread with a completely different subject; instead, start your own thread.

---

### Post by crazyfuturamanoob on 2010-09-07
> **cascade9 said:**
> Unless I'm mistaken, HD4290 is onboard video only. Its an ATI chipset so you wont be able to run SLI (ATI is crossfire only). 

Even if you could run SLI, 2 7300GTs are still going to be very slow, even on games that have good SLI support. On games with poor/nonexistant SLI support, its going to be no faster than a single card. 

You'd be better of saving your money and buying a decent card.

Yes, HD4290 is integrated into the motherboard. I found the 7300GT from a dumpster :D It's 100% working.

I'm not going to get new video cards. I just want to put the unused video card in use.

7300 GT doesn't support CUDA but 4290 supports (??) ATI Stream. Unfortunately games don't seem to support neither of those.

---

### Post by cascade9 on 2010-09-09
> **crazyfuturamanoob said:**
> Yes, HD4290 is integrated into the motherboard. I found the 7300GT from a dumpster :D It's 100% working.

I'm not going to get new video cards. I just want to put the unused video card in use.

7300 GT doesn't support CUDA but 4290 supports (??) ATI Stream. Unfortunately games don't seem to support neither of those.

If you werent going to buy a new card, how would you get a 2nd 7300GT? 

CUDA and ATI Stream are not for gaming. They are meant to use the GPU for some tasks currently done by the CPU ;)

---

