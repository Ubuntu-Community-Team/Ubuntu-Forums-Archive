---
title: "Ubuntu 8.04 vs XP"
date: 2009-09-02
forum: General Help
---

### Post by ratss on 2009-09-02
I have my Heron and windows installed in 1 drive on P4 2.0 socket 478 cpu with 512 ddr2.
comparing their performance, I curious about several things..
1- each time I start ubntu, it spend more than 95% CPU and 50% memory usage base on System Monitor preview, but less in windows. therefore my windows always faster than ubntu.
2- what exactly happen when using several OS in 1 drive..
for anyone that might be have the answer, thanks for your share..

---

### Post by elewis on 2009-09-02
I would guess that you are operating under one of two scenarios:
1) Dual boot. That is that the machine either boots into Microsoft or boots into Ubuntu. Both are not available at the same time or
2) You are running a virtual machine in which case you boot into one operating system and then boot into the other with a virtual machine such as Virtualbox.
Please specify which scenario under which you operate. In the case of virtual machine, are you booting in to Microsoft and then running Ubuntu under a virtual machine or are you booting into Ubuntu and then running Microsoft under a virtual machine.
In my case, I run a virtual machine. I boot into Ubuntu and then start Microsoft XP within the virtual machine. Under this scheme, the performance of Microsoft is at least as good in terms of speed as it is under native boot. Microsoft appears much more stable under Virtualbox than it does under a native boot.

---

### Post by Bucky Ball on 2009-09-02
Older disk (IDE) you might notice some diff due to where they are on the drive. SATA not so much. First partition is going to be fastest, last slowest.

---

### Post by theozzlives on 2009-09-02
If you installed Ubuntu under Windows (WUBI), you have Windows overhead running in the background slowing down Ubuntu.

---

### Post by Vaphell on 2009-09-02
system monitor in Ubuntu is notoriously bad at reporting real load (it ads a lot itself for some unknown reason)
you get more reliable results by using top command in terminal

also remember that you compare modern system (Ubuntu) with an old one (XP)

---

### Post by ratss on 2009-09-03
> **elewis said:**
> I would guess that you are operating under one of two scenarios:
1) Dual boot. That is that the machine either boots into Microsoft or boots into Ubuntu. Both are not available at the same time or
2) You are running a virtual machine in which case you boot into one operating system and then boot into the other with a virtual machine such as Virtualbox.
Please specify which scenario under which you operate. In the case of virtual machine, are you booting in to Microsoft and then running Ubuntu under a virtual machine or are you booting into Ubuntu and then running Microsoft under a virtual machine.
In my case, I run a virtual machine. I boot into Ubuntu and then start Microsoft XP within the virtual machine. Under this scheme, the performance of Microsoft is at least as good in terms of speed as it is under native boot. Microsoft appears much more stable under Virtualbox than it does under a native boot.

actually, I did install XP first than I boot in to ubuntu Live CD to install ubuntu in different partition, in that case I tought it is a good idea to seperate OS in to dual boot mode, so it would be a minimum risk for them to affect each other.

---

### Post by DeMus on 2009-09-03
> **ratss said:**
> actually, I did install XP first than I boot in to ubuntu Live CD to install ubuntu in different partition, in that case I tought it is a good idea to seperate OS in to dual boot mode, so it would be a minimum risk for them to affect each other.

Is Ubuntu really slower or do you think it is slower because it uses more memory and CPU load?
If it is the last I would only be happy that Ubuntu uses more memory: that is why you bought it. When you buy memory and it is not used you wasted money, right?
Try to measure with top (started in a terminal) to compare the two again and then tell us the exact differences. It's always good to know real experiences instead of guesses and predictions.

---

### Post by ratss on 2009-09-03
> **DeMus said:**
> Is Ubuntu really slower or do you think it is slower because it uses more memory and CPU load?
If it is the last I would only be happy that Ubuntu uses more memory: that is why you bought it. When you buy memory and it is not used you wasted money, right?
Try to measure with top (started in a terminal) to compare the two again and then tell us the exact differences. It's always good to know real experiences instead of guesses and predictions.

Well.. I said that because the System Monitor said that too

---

### Post by Vaphell on 2009-09-03
he wanted to say that higher load numbers don't mean necessarily that system is proportionally slower. There is some correlation but it's not so simple.
Ubuntu is more complex so it requires slightly more power than several years old XP.

If you have plenty of ram available it doesn't really matter if memory usage is visibly higher. Problems start when load is so high that system trashes HDD all the time to swap.
CPU meters is somewhat more reliable, because apps can use only what is left after OS did its thing. But as it was pointed out avoid using System Monitor (unreliable results), use top in terminal instead.
My 4 yrs old desktop (AMD64 3000 with 1,5GB RAM) sits under 5% of cpu and at 30-50% of RAM.

---

