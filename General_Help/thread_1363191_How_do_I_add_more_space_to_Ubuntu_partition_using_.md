---
title: "How do I add more space to Ubuntu partition using Gparted?"
date: 2009-12-24
forum: General Help
---

### Post by sotoj159 on 2009-12-24
I have a laptop that came with windows vista installed.  Later, I installed Ubuntu on a 25gb partition.  I have used up 23gb, so I would like to take another chunk of vista to add to Ubuntu (about 30gb).  I've been trying to do this using the Ubuntu cd because it has Gparted, but have not succeeded.  I have also searched online for answers, but they only teach you how to partition your linux hard drive (at least from what I understand...i'm pretty new with linux in general).  Also, from those 30gb, I would like to add more space to the swap area.

I would like to do this without loosing information from my drive (so basically, without having to format my drives), but just in case, I will definitely be making a backup of a bunch of my stuff on there (just to be safe).

So...anyone?  Replies will be greatly appreciated  :)

---

### Post by indytim on 2009-12-24
We're kind of at a disadvantage not knowing what the layout of your hard drive is.

The basics are to:
1.  Shrink your vista partition down to a safe level (in other words, don't be too aggressive as it will require additional space to maintain operability).  I'm not a Windows expert, but this may have to be done within the Windows built-in partitioner vs GParted).
2.  With the newly created unallocated space, you would expand the existing Ubuntu partition into this space.  You will do the same for the swap.

If you have a conflict such that the existing swap is blocking expansion of the Ubuntu partition, then you will have to move the swap to the left hand side of the new space first, then shrink the swap down to the level you want ultimately.  The final step in this scenario is to expand your Ubuntu.

**If you are using GParted for the above, DO THESE STEPS ONE AT A TIME TO COMPLETION.  DO NOT GANG THE OPERATIONS TOGETHER.**.

As you have indicated, make sure you have a good disaster recovery process in hand if things go badly (they shouldn't).

Hope this helps you get started.

IndyTim

---

### Post by sotoj159 on 2009-12-24
> **indytim said:**
> We're kind of at a disadvantage not knowing what the layout of your hard drive is.

The basics are to:
1.  Shrink your vista partition down to a safe level (in other words, don't be too aggressive as it will require additional space to maintain operability).  I'm not a Windows expert, but this may have to be done within the Windows built-in partitioner vs GParted).
2.  With the newly created unallocated space, you would expand the existing Ubuntu partition into this space.  You will do the same for the swap.

If you have a conflict such that the existing swap is blocking expansion of the Ubuntu partition, then you will have to move the swap to the left hand side of the new space first, then shrink the swap down to the level you want ultimately.  The final step in this scenario is to expand your Ubuntu.

**If you are using GParted for the above, DO THESE STEPS ONE AT A TIME TO COMPLETION.  DO NOT GANG THE OPERATIONS TOGETHER.**.

As you have indicated, make sure you have a good disaster recovery process in hand if things go badly (they shouldn't).

Hope this helps you get started.

IndyTim


Ok, thanks.  I will try doing the steps one at a time.  Before, i was trying to do them all together.  I will reply later and tell you how it goes.

---

### Post by sotoj159 on 2009-12-26
Well, I still don't know how to do it.  I took out another partition from my C drive in vista, but i don't know how to "add" it to my existing ubuntu partition.  Since I don't know how to do that, I tried to just format that partition into an ubuntu format so that I could just dump all the Ubuntu files that I want onto it, in order to free up space, but I can't.  It says that I don't have permission to do that.   :(

---

### Post by zaphod777 on 2009-12-26
can you post a screenshot from gparted?

You probably need to move remove the newly formated space unlock the swap move it to the far right and then resize the ubuntu partition. But do it with a live cd so you wan't be accessing the ubuntu partition.

Also just to be on the safe side you have a backup right?

---

### Post by steveneddy on 2009-12-26
Download and use the Gparted Live CD.

You cannot partition a HD that you are using, it must not be operational while partitioning, which is why the Live CD will get your task completed.

Or you could use the partitioning software that is part of Windows.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by sotoj159 on 2010-01-03
I'm sorry I've taken so long to answer, but I was on vacation and got back on friday.  I do not have this problem anymore, because as my luck would have it, I left my laptop unattended on the arm of the couch, and slowly but surely, fell and damaged the hard drive :oops:.  Luckily, I did backup my stuff (music and some other files) before I left, so they are safe on my cousin's desktop.  Because of this incident, what I have set up right now is the external hard drive running ubuntu.  Now I just have to buy a replacement HDD from ebay and wait :(.

---

