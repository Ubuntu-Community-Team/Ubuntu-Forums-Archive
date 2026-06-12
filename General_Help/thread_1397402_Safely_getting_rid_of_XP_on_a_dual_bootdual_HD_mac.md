---
title: "Safely getting rid of XP on a dual boot/dual HD machine"
date: 2010-02-03
forum: General Help
---

### Post by rimshot4 on 2010-02-03
I have XP on my IDE hard drive and Ubuntu on my USB hard drive (which is really an IDE drive with a USB adapter and external power souce). We've used Windows once in the past month, so we decided to jettison it. Two questions.

1. Can we simply delete all partiitions on the IDE hard drive and reformat or will this cause problems? 
2 Is the write-speed gain worth switching the drives out, putting the Ubuntu drive in my IDE slot and my freshly wiped drive on the USB adapter? Can I physically switch the drives out without causing OS problems?

---

### Post by audiomick on 2010-02-03
Hi.
first of all, I haven't done what you are talking about myself, so I can only pass on what I have read without having tested it.

to the first question, in principle, yes, you can just re-format the windows partition and make it available to your Ubuntu install.
There is info here:
[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

The problem with that is that it is talking about grub legacy that was used up until 9.04. If your install was fresh installed as 9.10, you will have grub2.
Info about editing that here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

to the second point, I would expect a speed increase if you put the Ubuntu drive into the machine instead of in a USB housing, but I don't know for sure.

I would suggest doing the partition work on the windows drive, then swapping, then trying the grub repair. I think if you repair grub then move the drives around, grub will get confused.

What might also catch you out is if the existing grub is in the mbr of the drive with windows on it, not on the one with ubuntu on it. I can't say how likely that is, or how much stress that could cause you.


When you have done the partition work and changed the drives around, you might want to follow the instructions here to find out what you have got where (before trying the grub repair. No point in doing that if Grub has disappeared.)
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
The output shows you pretty much all there is to know about what is on which partition where, where the boot loader(s) is(are) and where it is pointing to.

I hope this helps.

---

### Post by howefield on 2010-02-04
> **rimshot4 said:**
> I have XP on my IDE hard drive and Ubuntu on my USB hard drive. We've used Windows once in the past month, so we decided to jettison it.

Unless you need the space, it might be worth keeping. You might want to use it twice next month. :)

But in any event, the speed of your operating system should benefit significantly by being on the IDE drive rather than USB. Not only that, your cpu will not spend so many cycles running USB traffic and may run cooler.

> 1. Can we simply delete all partiitions on the IDE hard drive and reformat or will this cause problems?

Depends on where grub is, although this can be reinstalled with a live cd.
 
> 2 Is the write-speed gain worth switching the drives out, putting the Ubuntu drive in my IDE slot and my freshly wiped drive on the USB adapter? Can I physically switch the drives out without causing OS problems?

I'd say yes, definately. However, which is the faster drive ?

I'd use the fastest, newest drive for the operating system, and the other for data storage.

Given that you are going to fairly considerable effort, might be worth simply starting again, ie, saving all your data and reinstall Ubuntu to the drive of your choice, (with a seperate /home partition).

Although if it were me, I'd wait for 10.04 due in April and dual boot on a single drive.

---

### Post by rimshot4 on 2010-02-05
Both HDs were 40 gig and I'm getting a video capture card, so I definitely needed the space. I'm trying to put off buying a 160gb as long as possible :p

The procedure went without a hitch. I now have a faster OS on my internal drive and a blank external. Thanks for the help!

---

