---
title: "Slow dd?"
date: 2009-08-11
forum: General Help
---

### Post by MichiGreat on 2009-08-11
**Hi!**

If I want to create a file with random content using
```
dd if=/dev/random of=zufall bs=10 count=20
```
I experience two things that make me wonder:
1st: If I let it read/write 10 bytes for 20 times, the file should have 200 bytes, shouldn't it? Indeed, it has only 165 bytes. With bs=1000 count=1 and bs=4000 count=1 it has in both cases 128 bytes.
2nd: This command just took 54 seconds! Interestingly, this is not limited to Ubuntu, and not even to Linux, I experienced the same in NetBSD 5, where the same command took 276 seconds (ran in a VMware virtual machine on a AMD64 X2 5000+ CPU), but in NetBSD it creates a file with a size of 200 byte, as expected (whereby bs=8000 count=1 creates a file with 30 bytes :confused:).

My system is Xubuntu 8.04.3, but that shouldn't matter.

Any comments greatly appreciated!

Regards,

*Michael*

---

### Post by Insightfill on 2009-08-11
Well, dev/random will try to give 'truly' random bits from an internal pool, and will stall if it uses up all the bits and wait for new ones to get created.  Try doing a "cat /dev/random" and watch how it will go pretty quickly, then slow down for a while.

Unless true security is your goal, consider just using /dev/urandom, which is pseudo-random and usually good enough.

Not sure about the small file size, but will explore.

---

### Post by MichiGreat on 2009-08-11
> **Insightfill said:**
> Unless true security is your goal, consider just using /dev/urandom, which is pseudo-random and usually good enough.

Thanks a lot for your reply! /dev/urandom works perfectly, both in Linux and NetBSD, and behaves as expected.

---

### Post by Insightfill on 2009-08-11
> **MichiGreat said:**
> Thanks a lot for your reply! /dev/urandom works perfectly, both in Linux and NetBSD, and behaves as expected.

Glad to hear it!!  I've played with it a little as you did, and it appears that /dev/random is timing out when fed into dd, which is why you don't ever get a full file.

Whole schools of thought and research into this /dev/random thing - worth some spare time reading.  I especially like going to "random.org" for 'fun' sometimes.

---

