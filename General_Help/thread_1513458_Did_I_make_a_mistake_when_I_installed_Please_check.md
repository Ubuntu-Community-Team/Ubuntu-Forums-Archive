---
title: "Did I make a mistake when I installed? Please check ASAP. Might be a simple problem."
date: 2010-06-19
forum: General Help
---

### Post by inimitablesikh on 2010-06-19
Hey, I just installed 10.04 64 bit yesterday, and all i did was install it on a 20 GB Ext4 partition I made, mounted at /

I didn't make a partition at /home or swap I wasn't sure if those were necessary or if I needed those. Do I? I have 4 GB RAM, 2.4 GHZ Core 2 Duo, Nvidia 8600 mobile, and it's a laptop.

Could this be the reason suspend doesn't work for me? When I press suspend, it seems as if it's going to sleep mode, but it comes back on and goes to the lock screen.

---

### Post by tgm4883 on 2010-06-19
No, you did fine. You can install everything to / without a /home. Suspend not working is due to something else.

---

### Post by inimitablesikh on 2010-06-19
> **tgm4883 said:**
> No, you did fine. You can install everything to / without a /home. Suspend not working is due to something else.

Okay. I'm still getting familiar with Ubuntu, so another question. What is the purpose of swap and when would you need it? Also, what is the purpose of a /home partition?

---

### Post by ajgreeny on 2010-06-19
> **inimitablesikh said:**
> Okay. I'm still getting familiar with Ubuntu, so another question. What is the purpose of swap and when would you need it? Also, what is the purpose of a /home partition?
Swap is in some ways a relic of when computers had only small amounts of RAM.  With 4GB ram you will be able to run the system perfectly well.

It is just like the virtual memory in windows and will allow any overflow of memory onto the hard disk when your RAM modules are fully used.

It is also used when you hibernate your system, the whole system going onto the swap partition, therefore if you have no swap, you will not be able to hibernate.  I don't think this affects suspend, so should not have anything to do with that problem.

---

### Post by inimitablesikh on 2010-06-19
> **ajgreeny said:**
> Swap is in some ways a relic of when computers had only small amounts of RAM.  With 4GB ram you will be able to run the system perfectly well.

It is just like the virtual memory in windows and will allow any overflow of memory onto the hard disk when your RAM modules are fully used.

It is also used when you hibernate your system, the whole system going onto the swap partition, therefore if you have no swap, you will not be able to hibernate.  I don't think this affects suspend, so should not have anything to do with that problem.


Ah, okay I understand. I know what swap is because of android, but I wanted to make sure. Would you guys know why suspend isn't working, because suspend is essentially the equivalent of sleep on windows and it shouldn't require space

---

