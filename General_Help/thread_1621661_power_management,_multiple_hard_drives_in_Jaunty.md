---
title: "power management, multiple hard drives in Jaunty"
date: 2010-11-14
forum: General Help
---

### Post by InvisibleMan on 2010-11-14
I have a dual boot system (HD0=WinXP, HD1=Jaunty). I recently added a third hard drive on the second IDE controller so HD2 (data-only, NTFS) is in the slave cable position with a CD drive on the master position on the second IDE cable.

In both XP and Jaunty, I had previously set my system to "sleep" or hibernate after 30 minutes of inactivity. I added the third hard drive and this still works. However, as an added unexpected bonus, the third hard drive appears to power itself down after 30 minutes if I don't access it even while I'm using Jaunty to do my work.

I like this, but it puzzles me. I had assumed that all drives would remain up and running while I was working. Furthermore, I can't find anything in my config files or system settings that would cause this sleepy behavior to be the case.

Any ideas, anyone?

---

### Post by sikander3786 on 2010-11-14
Find out your HDD and use this command to disable HDD idle.

```
sudo hdparm -S 0 /dev/sda
```

Replace sda with your drive.

To find your drive,

```
sudo fdisk -l
```

Good Luck!

---

### Post by InvisibleMan on 2010-11-15
You miss the point. I like the fact that HD2 hibernates. I do not want to change that.


The question is: Why is it hibernating after 30 minutes? Or: why is HD2 hibernating after 30 minutes while HD0 and HD1 are still up and running?

---

### Post by sikander3786 on 2010-11-16
> **InvisibleMan said:**
> You miss the point. I like the fact that HD2 hibernates. I do not want to change that.


The question is: Why is it hibernating after 30 minutes? Or: why is HD2 hibernating after 30 minutes while HD0 and HD1 are still up and running?
The answer simply might be no activity on HD2. HD0 and HD1 might contain the Ubuntu root partition, Swap, /home therefore they are being used when you use your computer. No such activity on HD2.

You know better about your setup. HDD will not hibernate until it is left inactive for 30 min. Simple as that.

---

### Post by InvisibleMan on 2010-11-16
InvisibleMan originally wrote "The third hard drive (HD2) appears to power itself down after 30 minutes if I don't access it even while I'm using Jaunty [from HD1]."


Sikander3786 wrote "The answer simply might be no activity on HD2."


InvisibleMan repeats:

"I had assumed that all drives would remain up and running while I was working. Furthermore, I can't find anything in my config files or system settings that would cause this sleepy behavior to be the case.

Any ideas, anyone?"


To state it plainly: I understand that HD2 is not being accessed. In fact, that is exactly what I wrote in my original question. 

I'll repeat myself once more. My question is "Why does this hard drive (HD2) hibernate without me specifically having told it to hibernate? Where in the config files or system settings is the command telling this hard drive (and this hard drive only) to hibernate while the other hard drives are in use?"

---

### Post by InvisibleMan on 2010-11-20
Bump.

And please, just read the original post. Don't half-read it and then decide to answer some version of what you think I asked. I think that ground has already been covered.

---

