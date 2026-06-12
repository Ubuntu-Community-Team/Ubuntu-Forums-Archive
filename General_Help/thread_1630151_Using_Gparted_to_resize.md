---
title: "Using Gparted to resize"
date: 2010-11-24
forum: General Help
---

### Post by lsutiger on 2010-11-24
Attached are two screen shots.

I have a lot of unallocated space on this new drive that I would like to resize the third partition into.
As you can see, the unallocated space and the third partition are right next to each other with no space in between. Yet when I go to resize the third partition, I can not grow it. Is there a trick to this?

I booted on the Gparted live cd when doing this.

---

### Post by wojox on 2010-11-24
Resize /dev/sda2

---

### Post by Quackers on 2010-11-24
You cannot extend sda6 because it is part of an extended partition (sda2) and that partition is full.
If you first extend sda2 you should then be able to extend sda6.
I would suggest only doing one job at a time though.
Good luck :-)

---

### Post by lsutiger on 2010-11-24
Geesh! I feel like slapping myself upside the head! LOL
I guess somedays you are the pigeon, others you are the statue, hehe
Thanx for the answer!

---

### Post by Quackers on 2010-11-24
You're welcome :-)
I assume you managed it then :-)

---

### Post by lsutiger on 2010-11-28
Yes it did...had a long day coding and was burnt....thanx for your insight!

---

### Post by tajiknomi on 2010-11-28
> **lsutiger said:**
> Yes it did...had a long day coding...

[SIZE=2]Can you let me ***know*** about that ***coding*** how you Resize your Extend partition, i haven't did it yet...moreover, Is that ***similar*** resizing like other drives ? or some ***advanced*** coding is required ...?[/SIZE]




*[SIZE=2]Moreover,you forgot to mark thread as solved[/SIZE]* ;)

---

### Post by lsutiger on 2010-11-28
I was working on an app for work all day, so the coding had nothing to do with this.
I used the live cd of Gparted which you can [get here]("http://gparted.sourceforge.net/").

And it was simple enough, I just wasn't thinking....

---

### Post by tajiknomi on 2010-11-29
> **lsutiger said:**
> I was working on an app for work all day, so the coding had nothing to do with this.
And it was simple enough, I just wasn't thinking....


OOps, ithought the coding was for resizing :D

---

