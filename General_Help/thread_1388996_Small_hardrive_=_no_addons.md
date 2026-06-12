---
title: "Small hardrive = no addons?"
date: 2010-01-23
forum: General Help
---

### Post by Joey B. on 2010-01-23
I'm unable to get any addons from the Software Center because I installed Ubuntu on my D-Drive. Anything than can help?

---

### Post by Joey B. on 2010-01-23
I am a thread killer. -_-

---

### Post by Miljet on 2010-01-23
Sure ain't much information to go on. What size is the disk Ubuntu is installed on? Try posting the results of ```
sudo fdisl -l
```
What version Ubuntu? How did you install?

---

### Post by Joey B. on 2010-01-23
My current disk size after shrinking I'm not sure, but before it was at least over 100. And it's the 9.10 version. I installed by shriking my D-Drive and using my disk I had burned, I entered everything it told me to.

---

### Post by audiomick on 2010-01-23
> **Miljet said:**
> Sure ain't much information to go on. What size is the disk Ubuntu is installed on? Try posting the results of ```
sudo fdisl -l
```
What version Ubuntu? How did you install?
Typo!!
that's 
```
sudo fdisk -l
```
the last character is a lower case L, not a figure one.

---

### Post by Leppie on 2010-01-23
> **Joey B. said:**
> I'm unable to get any addons from the Software Center because I installed Ubuntu on my D-Drive. Anything than can help?
what does this mean? did you do a wubi install? in ubuntu there's no "D-Drive"...

---

### Post by Joey B. on 2010-01-23
My computer has an extra drive built it, the D or Data drive. I installed it into this because I had absolutely no space to shrink on my C Drive.

---

### Post by Joey B. on 2010-01-23
God, I** AM** a thread killer.

---

### Post by CharlesA on 2010-01-23
How much space is left on yer drive?

---

### Post by Joey B. on 2010-01-23
55.5 GB I believe is what it said last time I was on Windows.

---

### Post by Joey B. on 2010-01-23
Do I have to continually bump this up to get some help?

---

### Post by CharlesA on 2010-01-23
This is a forum, not IM. You don't need to go nuts bumping the thread every 15 minutes.

Did you install it using Wubi?

---

### Post by Joey B. on 2010-01-23
I had my cousin( He may be a member on here) tell me what to do when I was over at his house last, I did what he said, just partion a drive, install on the partioned drive and you've got a dual boot.

---

### Post by CharlesA on 2010-01-23
Ok. How big is the partition you created?

```
sudo fdisk -l
```

---

### Post by Joey B. on 2010-01-23
It's 59.5 GB.

---

### Post by CharlesA on 2010-01-23
So, what's the problem? You've got plenty of space.

---

### Post by Joey B. on 2010-01-23
Never mind, I removed some programs I would never need. I have at least one download available.

---

### Post by CharlesA on 2010-01-24
I don't understand. First you said that you installed ubuntu on the "D" drive, then you said that you did a dual boot.

Did you install it from inside windows?

---

### Post by Joey B. on 2010-01-24
I booted off a CD after shrinking my D-Drive to half so I could partion Ubuntu with Windows.

---

### Post by CharlesA on 2010-01-24
Ok. Um.. a normal ubuntu desktop install takes up around 5-8GB of space. How big did you make the partition? If it's 55 GB, you definitely have plenty of space.

You never did post the output of sudo fdisk -l.

---

### Post by Joey B. on 2010-01-24
I can not post it do it right now because I'm busy right now. I will when I can.

---

