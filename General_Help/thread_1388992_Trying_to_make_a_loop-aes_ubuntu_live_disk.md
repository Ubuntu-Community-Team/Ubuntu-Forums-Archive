---
title: "Trying to make a loop-aes ubuntu live disk"
date: 2010-01-23
forum: General Help
---

### Post by Wipster on 2010-01-23
Hi all, I have spent the last two days hanging out on irc reading documentation twiddling my thumbs while a kernel compiles for the nth time, and I'm exhausted and need a hand.

I am trying to make a live cd with the module loop-aes installed, doesn't sound too tricky does it, my processes thus far have been.
Make a basic livecd with these instructions: [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
Then compile a new kernel with CONFIG_BLK_DEV_LOOP=m not y (why was that changed grrr) as per these instructions: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
I then add a debian repo to get the source for loop-aes and use the module-assistant to build and install it.
I am on the home straight now.... but whats this 2.2gig? Well your not going to fit on a cd are you ;) 
How on earth can I remove the programs which where installed as deps so I could build this kernel? I have removed the main ones I needed to install but the others are still there sigh.

Much thanks,
Wip

---

### Post by Wipster on 2010-02-02
Anyone able to shed some light on this? I have tried just building the cd image from basics and I find it has loads of errors and doesn't work well. I have even taken the ISO of the current release and extracted and updated the packages and it seems to not very well either, is there some special magic I am missing?
A simple package update from a working source should have been a recipe for a no error image.

---

### Post by audiomick on 2010-02-02
> **Wipster said:**
> ...I am on the home straight now.... but whats this 2.2gig? Well your not going to fit on a cd are you ;) 


why not put it on a DVD? It would fit, wouldn't it?

---

### Post by Wipster on 2010-02-02
> **audiomick said:**
> why not put it on a DVD? It would fit, wouldn't it?

Indeed it would, DVD be a bit slow tho wouldn't it? I'd rather not waste one if I can get away with it.

---

### Post by audiomick on 2010-02-02
> **Wipster said:**
> Indeed it would, DVD be a bit slow tho wouldn't it? I'd rather not waste one if I can get away with it.

I don't see why it would be any slower than a live CD, but I don't know for sure.

---

