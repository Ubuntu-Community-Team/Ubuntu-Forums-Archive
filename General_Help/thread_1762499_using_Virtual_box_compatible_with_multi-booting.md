---
title: "using Virtual box compatible with multi-booting?"
date: 2011-05-19
forum: General Help
---

### Post by eb3ha4el on 2011-05-19
Okay My question is a little bit complicated.
Try to clarify it, fact is:


1. I want to install linux as primary OS.

2. I want to use multi-booting option when starting computer for choosing between windows/linux

3. I want to use virtual box in linux to use windows. 

4. I want to use virtual box in windows to use linux.



Are these all 4 possible with single install of linux and windows respectively in 2 partitions?
if so, what should I do after installing ubuntu?

---

### Post by 3xp10r3r|X13 on 2011-05-19
[FONT=Courier New]Yes, it's all possible. :D

1. You install windows

2. You install ubuntu next to windows

3. Install virtual box in both operating systems

4. Install your wanted operating system in the version of virtual box you want to use


Any questions?
[/FONT]

---

### Post by eb3ha4el on 2011-05-19
Thank you

but will these two windows (or ubuntu) will share same data and personal configuration?
I mean the one in partition and another in virtual box.
If so, will this mean that they will take double space for any activities saved?

---

### Post by 3xp10r3r|X13 on 2011-05-19
[FONT=Courier New]If you're using windows in ubuntu, you have to create a virtual partition of a certain size which is an nfts partition. 
Windows doesn't recognise ext3, so you won't be able to access any data on your actual drive(if not an external nfts drive)

So this is basically a yes unfortunately it works that way.

it's mostly the fault of !WINDOWS!, but I won't start discussign which one of them is better.

hope this helped :D
[/FONT]

---

### Post by eb3ha4el on 2011-05-19
> **3xp10r3r|X13 said:**
> [FONT=Courier New]If you're using windows in ubuntu, you have to create a virtual partition of a certain size which is an nfts partition. 
Windows doesn't recognise ext3, so you won't be able to access any data on your actual drive(if not an external nfts drive)

So this is basically a yes unfortunately it works that way.

it's mostly the fault of !WINDOWS!, but I won't start discussign which one of them is better.

hope this helped :D
[/FONT]


Thank you 
Yes... But I think I was wondering about 
whether the files and configuration between these 2 windows
which are one in virtual partition, and another in real partition
would share files and personal configuration and everything?



Also, would you say using windows through virtual box in ubuntu
will be very slow on Netbook?

---

