---
title: "Can wubi run if windows no work properly?"
date: 2012-06-11
forum: General Help
---

### Post by duranmla on 2012-06-11
Ubuntu Community,

Hi all, i want install Ubuntu but i have a HP Laptop that have 4 partitions by default C, HP_TOOLS, RECOVERY and SYSTEM, so i cant make another 2 partition, just one more (for data sharing win-ubuntu). So one of my mision is have Ubuntu OS in another place that it can run if windows fail and that this place have access to my folders (sharing partition).

Because i cant make another partition i want to know:

CAN I WUBI RUN IF WINDOWS CANNOT RUN PROPERLY?

i hope that someone can give me an answer. Thanks ^^

---

### Post by zombifier25 on 2012-06-11
I doubt it. If Windows fails to boot properly then Wubi will be borked. If you want your Ubuntu to function without Windows being able to run, you should dual-boot.

I see you have pasted the partitions limit (4 partitions), so remove one of them, create an extended one and you can put how much partitions you want in there. Boot of an Ubuntu CD, run GParted, add an extended partition and then create an ext4 partition and whatever partitions in there.

---

### Post by wilee-nilee on 2012-06-11
> **duranmla said:**
> **CAN I WUBI RUN IF WINDOWS CANNOT RUN PROPERLY**?

No, and you can remove one partition if done correctly to put a extended in to contain the ubuntu and a swap.

4 primaries is the max, or 3 primaries and an extended.

Situations like yours are dealt with every day to have a dual boot on this forum.

---

### Post by duranmla on 2012-06-11
Thanks for answer, now i try to stand how i can do your suggestions. 

The problem is that: partition SYSTEM, HP_TOOLS and RECOVERY, cant be delete (i think so) because i need it if something happened in the future with my windows.

---

### Post by zombifier25 on 2012-06-11
Then good, sounds like the last one can be deleted. What are you using the last one for?

---

### Post by wilee-nilee on 2012-06-11
> **duranmla said:**
> Thanks for answer, now i try to stand how i can do your suggestions. 

The problem is that: partition SYSTEM, HP_TOOLS and RECOVERY, cant be delete (i think so) because i need it if something happened in the future with my windows.

Do a full image of the operating system off the computer, the recovery can be infected as well. You are allowed at least one backup disc set with a less then pro version of W7, make a recovery disc as well in backup and recovery as well immediately, if you have no install disc. You can make images with a number of free cloners on a external HD.
 
The HP tools are just fluff generally, back up everything before doing anything.

You might start with a virtualbox while figure out what to do, the vdi can be used on any vbox.

---

### Post by duranmla on 2012-06-11
The last one: RECOVERY is for have a system image if you need back to default settings, i mind that if my Laptop no working good i can use RECOVERY for restart like when i bought it

---

### Post by duranmla on 2012-06-11
> **wilee-nilee said:**
> 
You might start with a virtualbox while figure out what to do, the vdi can be used on any vbox.

Thanks, but i want the dual boot. You say that i make recovery off the computer and them delete this partition? Sounds good but is better if i can keep with my original partitions. :$

------------------------------------------------------

What is your opinion about this: [http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/Tip-amp-Trick-How-to-partition-H-D-D-in-Preloaded-Windows-7/td-p/143741](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/Tip-amp-Trick-How-to-partition-H-D-D-in-Preloaded-Windows-7/td-p/143741)

---

### Post by wilee-nilee on 2012-06-11
> **duranmla said:**
> Thanks, but i want the dual boot. You say that i make recovery off the computer and them delete this partition? Sounds good but is better if i can keep with my original partitions. :$

------------------------------------------------------

What is your opinion about this: [http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/Tip-amp-Trick-How-to-partition-H-D-D-in-Preloaded-Windows-7/td-p/143741](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/Tip-amp-Trick-How-to-partition-H-D-D-in-Preloaded-Windows-7/td-p/143741)

The instructions are from a windows point of view, you would never make a partition for linux in windows.

I can appreciate you having wants as far as your computer goes, but there are alternatives that you will have to deal with.

I don't really have the patience to go step by step on a walk through of explaing every little bit.  Many do though so you will get what you want, as far as a dualboot just probably not the exact way you want it.

Make sure that you are backed up besides the recovery at this point, do not rely on that, it can get knocked out of the picture, by getting infected it is on the same HD as the main windows, or just being able to boot it with a new OS installed.

---

### Post by duranmla on 2012-06-11
> **wilee-nilee said:**
> 
I don't really have the patience to go step by step on a walk through of explaing every little bit.  Many do though so you will get what you want, as far as a dualboot just probably not the exact way you want it.

Well, thanks man, so what i done will be create a virtual machine and try to do this in a virtual machine. Because you say that i can do that i want. 

^^

---

### Post by wilee-nilee on 2012-06-12
> **duranmla said:**
> Well, thanks man, so what i done will be create a virtual machine and try to do this in a virtual machine. Because you say that i can do that i want. 

^^

You will have to learn this like the rest of us through trial and error I suspect. 

Nobody led me by the hand through this, I would not have asked anyone to begin with. I am a research minded person basically.

What you may have missed here though is the importance of good backups so that this learning process is insured to not destroy your basic set up. 

Do not rely on the windows recovery completely, is my advice there are to many variables;

The virtual is an excellent way to get started, you have the set up on a virtual machine, that can be transferred to another computer if needed easily. While you're actually using Ubuntu you can lurk the forums ask questions until you are confident on how to do a actual dual boot if you want that.

In the end a self learning situation leaves you feeling more empowered possibly.

---

### Post by duranmla on 2012-06-12
> **wilee-nilee said:**
> You will have to learn this like the rest of us through trial and error I suspect. 

Nobody led me by the hand through this, I would not have asked anyone to begin with. I am a research minded person basically.

What you may have missed here though is the importance of good backups so that this learning process is insured to not destroy your basic set up. 

Do not rely on the windows recovery completely, is my advice there are to many variables;

The virtual is an excellent way to get started, you have the set up on a virtual machine, that can be transferred to another computer if needed easily. While you're actually using Ubuntu you can lurk the forums ask questions until you are confident on how to do a actual dual boot if you want that.

In the end a self learning situation leaves you feeling more empowered possibly.

Thanks for your time and words.

While i dont answer i can make the dual boot keeping SYSTEM, HP_TOOLS and RECOVERY. no i have this:

SYSTEM
C:
(Extended Partition): HP_TOOLS, RECOVERY with DATA (sharing data) and my distro. 

I hope that of this way i can make a RECOVERY when i want.

Thanks again, G8.

---

### Post by elliotn on 2012-06-12
dual boot gives u freedom as is one os dies u can still work on the other includes easy to backup your data

---

