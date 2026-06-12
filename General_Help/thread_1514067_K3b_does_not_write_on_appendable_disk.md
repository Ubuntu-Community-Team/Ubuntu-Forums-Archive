---
title: "K3b does not write on appendable disk"
date: 2010-06-20
forum: General Help
---

### Post by Rogierdg on 2010-06-20
I have Ubuntu 10.04 installed on my Armada laptop with a Teac CD-W24E internal and a Plextor-DVDR PX504A via USB.
I use K3B for writing CD data projects to 700mb CD-RW 1-4x discs. K3B writes ok on both drives if the inserted disk is a blank disk. If I insert an appendable disk with lots of space left, it asks to blank it before writing. I find no way to write on an appendable disk with K3B. Is this a software limitation or am I missing something?
Thanks for any advice

---

### Post by bobcollard on 2010-06-20
> **Rogierdg said:**
> I have Ubuntu 10.04 installed on my Armada laptop with a Teac CD-W24E internal and a Plextor-DVDR PX504A via USB.
I use K3B for writing CD data projects to 700mb CD-RW 1-4x discs. K3B writes ok on both drives if the inserted disk is a blank disk. If I insert an appendable disk with lots of space left, it asks to blank it before writing. I find no way to write on an appendable disk with K3B. Is this a software limitation or am I missing something?
Thanks for any advice
Try Brasero, it should be a choice, not a requirement to blank the Disc.

---

### Post by jmszr on 2010-06-20
Rogierdg,

Did you try "Further actions" > Continue Multisession Project? Perhaps that will work.

---

### Post by Rogierdg on 2010-06-20
Brasero does not even recognise my Teac drive, and has the same problem with appendable disks. Even if you write to a blank disk with the option appendable in the burn dialogue, Brasero will not accept that disk for a new data project, sees it as full, with no space left, and requires a blank disk. So that is why i switched to K3B, in the hope of succes. Well, K3B recogises my Teac drive allright, but does not allow appends eather.
 
The multisession capabilities of K3B (first writing with option start multisession, and second with option continue multisession), result in a detection of a appendable disk after the first recording and a request to eject it with no further action!!
 
Seems to be a problem with appendable disks in general

---

### Post by Rogierdg on 2010-06-22
After the last sw update that included a Brasero update, I can now burn multisession disks on my Plextor drive. Can still not achieve it with K3b.
Tks for the help

---

### Post by bobcollard on 2010-06-22
> **Rogierdg said:**
> After the last sw update that included a Brasero update, I can now burn multisession disks on my Plextor drive. Can still not achieve it with K3b.
Tks for the help
Glad it works for you now.  Please Edit your first post in the Title by adding [Solved] so others may benefit from your experience.

---

### Post by TimGS on 2010-07-01
This is not solved if **K3B** isn't working!

-- Tim.

---

### Post by bobcollard on 2010-07-01
> **TimGS said:**
> This is not solved if **K3B** isn't working!

-- Tim.
No, but, the alternative is working for the OP.  I suggest, if you wish to continue this thread, you start a thread of your own.

---

### Post by TimGS on 2010-07-12
The solution to the problem as titled in the forum thread - i.e. about K3B - is actually present upstream (its a bug in k3b 1.91 and has been solved in 1.92+) according to the k3b website and I have reported this to launchpad [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/600822](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/600822).

@Bob - sorry we disagree on this, but I have seen that too often problems on these forums are answered by telling people to use a different software package. My reasons for not liking this are that (often) the alternative suggested has its own drawbacks and more importantly this does not encourage genuine fixes to problems or bugs. Lastly, but significantly, it doesn't help to have thread titles reading "[SOLVED] K3b does not write on appendable disk" when you are searching for a genuine solution.

-- Tim.

---

### Post by bobcollard on 2010-07-12
Tim, I understand your point, it is not "Solved"  Per se.  I don't know how else the OP can state it unless he writes "Resolved."  Giving someone an alternative is common on all forums.  Especially when you know that works.   As for K3b, it does not work.  Take that up with their writers.
Regards, Bob

---

### Post by TimGS on 2010-07-12
> Especially when you know that works. As for K3b, it does not work.

You also have a point here in terms of the OP's specific problem, but on the other hand that is only half correct, and is part of my point about suggested alternatives having their own drawbacks. Not only do you *not *know that *any* other specific software works - but furthermore all the alternatives have their own bugs both reported and no doubt others waiting to be found.

So yes, this bug certainly implies that K3B 1.91 as in the Ubuntu repos does not work, but on the same basis neither does Brassero or any other software. The latter may do all that you (and many others) want, but to imply it 'works' and something else 'does not work' is misleading and just plain wrong.

-- Tim.

---

### Post by bobcollard on 2010-07-12
> **TimGS said:**
> You also have a point here in terms of the OP's specific problem, but on the other hand that is only half correct, and is part of my point about suggested alternatives having their own drawbacks. Not only do you *not *know that *any* other specific software works - but furthermore all the alternatives have their own bugs both reported and no doubt others waiting to be found.

So yes, this bug certainly implies that K3B 1.91 as in the Ubuntu repos does not work, but on the same basis neither does Brassero or any other software. The latter may do all that you (and many others) want, but to imply it 'works' and something else 'does not work' is misleading and just plain wrong.

-- Tim.
You may have the last word, LOL.

---

### Post by TimGS on 2010-07-12
OK, I will. :biggrin:

---

