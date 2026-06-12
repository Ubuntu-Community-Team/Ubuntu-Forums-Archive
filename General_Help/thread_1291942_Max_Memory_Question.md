---
title: "Max Memory Question"
date: 2009-10-15
forum: General Help
---

### Post by greenco on 2009-10-15
I am running Ubuntu v9.04 and I have two unused memory slots, on my motherboard. Can this version use 8 GBytes of memory? I have 4 GBytes installed now and can add two more sticks for a total of 8 GBytes (max for my motherboard).
Thanks

---

### Post by philinux on 2009-10-15
Depends if it's 64 bit.

Terminal.


```
uname -a
```

Mine is 64 bit.
 > uname -a
Linux philinux-karmic 2.6.31-14-generic #47-Ubuntu SMP Thu Oct 15 03:42:30 UTC 2009 **x86_64** GNU/Linux



What are your pc specs.

---

### Post by justleen on 2009-10-15
If you have 32-bits system , you could install the bigmem kernel.
That will give you the option to install more memory, without reinstalling the system with a 64bits ubuntu system.
Not sure if it is in the ubuntu repositories, but you could use the debian package.

---

### Post by greenco on 2009-10-15
uname -a gives me this.

inux coleman-desktop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

---

### Post by justleen on 2009-10-15
i686, which is 32 bits. 
So you will not be able to use more then 4GB of ram on this system.

---

### Post by greenco on 2009-10-15
Thanks for the quick replies!

---

### Post by P4man on 2009-10-15
Wondering why anyone needs more than 4GBs on ubuntu, unless you run multiple VMs simultaneously, I seem to have a bloody hard time using just 1 GB.

---

### Post by justleen on 2009-10-15
LoL @p4man

Im running on average 4 VM's (XP and 3 Lenny boxes at the same time, on a laptop with 2,5GB.. 

And thats still more then enough!

---

### Post by Giblet5 on 2009-10-15
> **justleen said:**
> If you have 32-bits system , you could install the bigmem kernel.
That will give you the option to install more memory, without reinstalling the system with a 64bits ubuntu system.
Not sure if it is in the ubuntu repositories, but you could use the debian package.

That uses PAE memory mapping. It can result in a noticeable decrease in performance as it will treat the physical RAM as logical pages of RAM and add an extra hurdle to memory access.

It's a workaround v a fix.

[Dan does a decent (and amusing) explanation]("http://www.dansdata.com/askdan00015.htm") of the incredibly retarded memory mapping that takes place in PCs.

---

### Post by P4man on 2009-10-15
I only got 2GB Ram in my desktop. Last time I was in the shop, i was stunned how cheap Ram had become, and I was tempted to pick up another 2 or 4GB, but I came to my senses and realized I am never ever swapping, and the only possible use I have for it is giving more ram to my Win 7 VM, but thats about to be deleted anyway. So I bought a bigger harddisk instead, you can never have too much diskspace :p

---

