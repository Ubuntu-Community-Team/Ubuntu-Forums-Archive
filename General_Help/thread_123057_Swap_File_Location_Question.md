---
title: "Swap File Location Question"
date: 2006-01-29
forum: General Help
---

### Post by Puptentacle on 2006-01-29
Since I'm soon going to be tossing the WinXP disc into the "old crap" drawer and going full Ubuntu this question came to mind tonight. This is more of a theoretical question than anything else.

Take the following situation: Two HD, one 80gb that (currently) is all Ubuntu. 20gb for the Ubuntu partition, 1gb of swap (for 512mb ram) and the rest for storage. Second drive is 120gb, 20gb for XP and the rest partitioned for storage. 

Would it decrease the response time to do the following?

[B]80gb drive
[/B]
Leave 20gb for Linux and use the rest for storage

[B]120gb drive
[/B]
Put the swap partition at the front of this drive and use the rest for storage. 

I'm asking because in my noob mind it seems that having the swap on a separate drive from the OS would speed up the response time somewhat since the disc head wouldn't be running from OS to swap and back during heavy load times.  

Would the OS even be able to operate with the swap separated?

Opinions? Pros and Cons?

---

### Post by heimo on 2006-01-29
Create swap partitions to both disks (preferrably near the beginning of the disks) and use same priority for both (in fstab file, see *pri *in *man swapon*). This way your system will use the one that's faster (less load). If you have enough memory, this won't make any significant difference, but it should be pretty much optimal.

---

### Post by Puptentacle on 2006-01-29
OOH! OK. 

This is more a "just how DOES this thing work, anyway" thread instead of a real worry about how the machine is going to run. I rarely hit the swap, just wondering...

So it would be the same size partition on each ie; double the RAM amount?

---

### Post by el3ktro on 2006-01-29
Depending on how much RAM you have, I would care about all this too much. I have 1GB of RAM, and I think my system never ever has used the swap partition. I would NOT recommend to have no swap at all, this is known to cause problems with some programs.

But in general, putting swap on a second HD is of course faster for the reason you mentioned.

Tom

---

