---
title: "which CPU should I use?"
date: 2011-08-28
forum: General Help
---

### Post by conradin on 2011-08-28
Hi Yall, 
I have 2 cpus around that fit my MotherBoard. one is a 64bit 3GHz dualcore Pentium with 2Mb of L3 Cache.

The other is a 32bit 3.2GHz dualCore Pentium with 1Mb L3 cache

I have a 4GB RAM limit on the board. So, which would be faster, assuming if I use the 64bit hardware I would Use the matching 64bit OS? 

most of my processing is the common stuff with some networking and Data recovery operations.

---

### Post by dino99 on 2011-08-28
my choice is 2MB cache + 4GB ram +generic-pae kernel (need a bios able to activate pae of course)

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by HereInOz on 2011-08-28
I reckon that you would need to put the two side by side as a comparison to actually tell the difference in speed.

The only thing which gives the advantage to the 64 bit processor is that the 64 bit system will see the full 4GB, if you are going to use 4GB of RAM, without the need to mess around with pae (physical address extension) kernels.

Apart from that, I reckon the two CPUs would be pretty similar in performance.

---

### Post by HereInOz on 2011-08-28
Hang on - are you sure that the 3.2GHz chip is a 32bit?  

I was not aware that Intel made any dual core (Core2Duo) processors which were 32 bit.  However, they did make 32 bit Hyper-threading Prescott CPUs which were actually single core, but looked like they were dual core in Windows because of the Hyper-threading, and they did make Centrinos which were 32 bit - for laptops, generally.

If your 3.2GHz processor is a Hyper-threading Prescott, and not a genuine Core2Duo processor, then it is quite old, and I would go with the 64 bit processor, no question about it.

---

### Post by cbowman57 on 2011-08-28
I know I haven't exactly kept up with hardware over the past few years but when did 32-bit & 64-bit processors become interchangable on the same motherboard?

---

