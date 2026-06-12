---
title: "Ext3 anti-fragmentation question!"
date: 2010-01-06
forum: General Help
---

### Post by Pipps on 2010-01-06
**Background**
I have decided to convert my separate media partition from NTFS to ext3, on the basis that it can be successfully accessed by Ubuntu by default, and by XP using [ext2fsd]("http://www.ext2fsd.com/"). 

**Issue**
I work with lots of big files >500MB. As ext3 does not provide the extents feature of ext4, I am concerned that some fragmentation may periodically affect disk performance.

**Noted**
I understand that using ext4 under these circumstances would be pointless, because the extents feature would be required to be disabled to allow compatibility using ext2fsd at this time, thereby removing any tangible ext4 benefit for my purposes.

**Question**
Would an effective method of disk optimisation and anti-fragmentation be to simply copy all files from the ext3 media partition across to another entirely separate empty backup ext3 drive, before copying them all back over to the ext3 media partition again?

Would this mean that when all the files are copied back again, they would be placed back in the 'correct and optimum order', so to speak?

Any thoughts, comments help and advice would be much appreciated. Thank you! :)

PS: I cringe in advance at the n00bs who are likely to reply to this thread with *'ext3 cannot become fragmented'*! :rolleyes:

---

### Post by Grenage on 2010-01-06
> Would this mean that when all the files are copied back again, they would be placed back in the 'correct and optimum order', so to speak?

Correct, the files should then be contiguous.

---

### Post by lotharmat on 2010-01-06
But ext3 cannot... become... fragmented... :wink:

---

### Post by Pipps on 2010-01-06
> **lotharmat said:**
> But ext3 cannot... become... fragmented... :wink:

Ohh... you big kidder... you! :mrgreen:

---

### Post by Pipps on 2010-01-06
> **Grenage said:**
> Correct, the files should then be contiguous.
Contigious! That is the right word! And that is perfect advice! Thank you! :D

---

### Post by Pipps on 2010-01-06
PS: Hello, both, from the UK! Guess you must be snowed-in too! :p

---

### Post by lotharmat on 2010-01-06
> **Pipps said:**
> PS: Hello, both, from the UK! Guess you must be snowed-in too! :p

Took 40 mins to make an 8 minute journey!

:evil:

---

### Post by Grenage on 2010-01-06
Aye, last night it took me 2 hours to drive 5 miles.  Today the roads were dead, only a few of us were mental enough to try the roads!

---

### Post by lotharmat on 2010-01-06
We got sent home at 1000 hrs yesterday but I stayed till 1245 hrs because all the roads were jammed - Why go home when work is warm and I can leave the heating down at home!

Today I thought bugger it! - I'm gonna work at one of the other offices! (My main base is 25 miles away)

I hate snow!

---

### Post by Pipps on 2010-01-06
I sympathise entirely!

I hear that in Norway, the winter blizzard season is often one of the most lucrative times for local farmers. 

The councils and local land-owners pay them to strap giant ploughs to the fronts of their tractors, and drive around sweeping the roads clean for all road-users 24/7.

If only our own local farmers were so proactive!

If only our local councils we allowed to use public money in such a useful and efficient way - rather than just wasting it or not spending it at all!

Sorry - all this snow makes me get a little hot-headed! :wink:

---

### Post by lotharmat on 2010-01-06
> **Pipps said:**
> ...

If only our local councils we allowed to use public money in such a useful and efficient way - rather than just wasting it or not spending it at all!

Or if they hadn't put all the money in Icelandic banks! :sad:

---

### Post by Pipps on 2010-01-06
Agreed! :-x

---

