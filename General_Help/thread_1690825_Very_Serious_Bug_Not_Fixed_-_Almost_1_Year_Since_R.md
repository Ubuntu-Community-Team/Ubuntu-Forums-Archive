---
title: "Very Serious Bug Not Fixed - Almost 1 Year Since Reported"
date: 2011-02-19
forum: General Help
---

### Post by ryannathans on 2011-02-19
Hello all

Ubuntu is awesome, I use it on my netbook all the time, plus I have an ubuntu 10.04 LTS server.

Only thing stopping me installing it on my desktop is this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259/)

Reported almost a year ago, and no word on anyone fixing it.

Cost me almost 500$ on a new motherboard (GA-P55a-UD5) a while back.

I can't find any progress or news regarding it.

What's the deal?

-Much Appreciated
ryannathans

---

### Post by dcstar on 2011-02-19
> **ryannathans said:**
> Hello all

Ubuntu is awesome, I use it on my netbook all the time, plus I have an ubuntu 10.04 LTS server.

Only thing stopping me installing it on my desktop is this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259/)

Reported almost a year ago, and no word on anyone fixing it.

Cost me almost 500$ on a new motherboard (GA-P55a-UD5) a while back.

I can't find any progress or news regarding it.

What's the deal?

-Much Appreciated
ryannathans

If **you** read the comments in the bug reports there are workarounds listed. The other option is to purchase a $20 LAN card.

---

### Post by DrFolger on 2011-02-19
This thread: [http://ubuntuforums.org/showthread.php?t=1022411&highlight=RTL8111%2F8168B](http://ubuntuforums.org/showthread.php?t=1022411&highlight=RTL8111%2F8168B)

One problem is that it needs to be redone everytime a kernel upgrade is pushed out.

---

### Post by ryannathans on 2011-02-19
> **dcstar said:**
> If **you** read the comments in the bug reports there are workarounds listed. The other option is to purchase a $20 LAN card.

Workarounds don't work for me. Purchasing a 20$ lan card would still cause ubuntu to fry my 2 lan ports which I must have for teaming in windows. There is a large bug that has existed for quite some time and therefore needs to be fixed. 

Ububtu is well known for its user simplicity and amazing record for everything to just 'work' out of the box. This should be consistent And not discriminate againt those useres who happen to have purchased hardware that has a bug that hasn't been fixed, even though it was reported almost a year ago.    Seeming this bug only occurs in ubuntu it mustn't be much to fix.

---

### Post by asmoore82 on 2011-02-20
I don't see anything on that bug report about "frying" anything.

---

### Post by ryannathans on 2011-02-20
> **asmoore82 said:**
> I don't see anything on that bug report about "frying" anything.


I have same problem as that bug but nothing can fix it, it just frys the chips. Had to buy a new mobo like I mentioned.

---

### Post by dcstar on 2011-02-20
> **ryannathans said:**
> 
..........
Ububtu is well known for its user simplicity and amazing record for everything to just 'work' out of the box. This should be consistent And not discriminate againt those useres who happen to have purchased hardware that has a bug that hasn't been fixed, even though it was reported almost a year ago.    Seeming this bug only occurs in ubuntu it mustn't be much to fix.

It is a **kernel** bug, Ubuntu uses Linux kernels like all other Linux distributions.

All the complaining in the world in this forum will not fix **kernel** bugs.

---

### Post by ryannathans on 2011-02-20
> **dcstar said:**
> It is a **kernel** bug, Ubuntu uses Linux kernels like all other Linux distributions.

All the complaining in the world in this forum will not fix **kernel** bugs.

So why is this issue not present in Fedora etc?

---

### Post by asmoore82 on 2011-02-20
> **ryannathans said:**
> I have same problem as that bug but nothing can fix it, it just frys the chips. Had to buy a new mobo like I mentioned.

makes no sense, you say:
 1. same as that bug
 2. frys chips

They can't both be true. That bug doesn't "fry" chips — I'm sure
someone wouldn't thought that important enough to comment on.

Have you tried reloading the firmware on these "fried" chips?

---

### Post by ryannathans on 2011-02-20
> **asmoore82 said:**
> makes no sense, you say:
 1. same as that bug
 2. frys chips

They can't both be true. That bug doesn't "fry" chips — I'm sure
someone wouldn't thought that important enough to comment on.

Have you tried reloading the firmware on these "fried" chips?

Reloading firmware? as in reflashing bios didn't help, i pulled power out for a day and it didn't work. nothing worked. the chips were stuffed.

Seems to be same issue as the bug though, but destroying the chips instead of needing a cold boot.

---

### Post by asmoore82 on 2011-02-20
> **ryannathans said:**
> Reloading firmware? as in reflashing bios …
No, not the BIOS.

Some modern cards have their firmware "exposed" to the OS.
This is so that driver updates can seamlessly update the card's firmware.

I don't have any experience with this myself but that's what I've heard.
So there's supposed to be software tools to correct a card "bricked" this way.
I want to say Intel writes this software to fix it as they always get credit
for manufacturing the northbridge on Intel boards.
For the price of a motherboard, I would definitely look into it.

---

