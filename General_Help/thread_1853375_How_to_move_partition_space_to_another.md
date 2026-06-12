---
title: "How to move partition space to another"
date: 2011-10-02
forum: General Help
---

### Post by sammya on 2011-10-02
Hey guys. Recently did a dual install of Ubuntu next to XP on my netbook. I only wanted to give the Ubuntu directory ~50gb but ended up halving the HDD by accident and was wondering if there was any way I could re-size/move the space on the ubuntu partition back to the xp?

I followed this guide found here for those who want a reference of exactly what I did. I just did the simple method (automatic partition, not manual)

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot") 

I booted up GPARTED in Ubuntu but couldn't find an option to move/re-size to another partition.

Ty

---

### Post by Quackers on 2011-10-02
Please install gparted and post a screenshot of its opening screen (if you have only one hard drive).

---

### Post by sammya on 2011-10-02
> **Quackers said:**
> Please install gparted and post a screenshot of its opening screen (if you have only one hard drive).

Booted the Ubuntu Live-CD via USB and in Gparted now. Chose the option to move/re-size the partition..currently in the process. 

So my plan basically was to shrink the volume which will leave me with unallocated space then boot XP where I would use a program I discovered called Partition Magic which can be used to merge unallocated space to an existing partitions. 

Any flaws in this action?

Cheers

[IMG]http://i51.tinypic.com/nx3wpw.png[/IMG]

---

### Post by Quackers on 2011-10-02
Yes :-(
That will take about 2 hours and will need to be done again.
If you'd allocated the new "free space" to be BEFORE sda5 you could have just shrunk the extended partition to match the new size of sda2 and then the free space would have been ouside of the extended partition (sda2). You could then have just extended the XP partition into that space.

Sadly you can't do that now, as the free space will be inside the extended partition and in between sda5 and sda6. 
For a partition to be extended in to free space it has to be next to that free space on the disc.

When you have finished what you are doing, you should make sure Ubuntu still boots, as moving a bootable partition carries a risk.
If it boots ok you should boot up the live cd again and move sda5 so that all the 92.63GB is in front of sda5 (another 2 hours or so) then shrink the extended partition (sda2) to match.
You can then extend the XP partition in to that space.

---

### Post by sammya on 2011-10-02
> **Quackers said:**
> Yes :-(
That will take about 2 hours and will need to be done again.
If you'd allocated the new "free space" to be BEFORE sda5 you could have just shrunk the extended partition to match the new size of sda2 and then the free space would have been ouside of the extended partition (sda2). You could then have just extended the XP partition into that space.

Sadly you can't do that now, as the free space will be inside the extended partition and in between sda5 and sda6. 
For a partition to be extended in to free space it has to be next to that free space on the disc.

When you have finished what you are doing, you should make sure Ubuntu still boots, as moving a bootable partition carries a risk.
If it boots ok you should boot up the live cd again and move sda5 so that all the 92.63GB is in front of sda5 (another 2 hours or so) then shrink the extended partition (sda2) to match.
You can then extend the XP partition in to that space.

Oh really? So I couldn't just merge the unallocated/free space to the existing partition xp is installed on?

Here is a screenshot from my disk manager inside xp:

[IMG]http://i54.tinypic.com/2vn4483.jpg[/IMG]

---

### Post by Quackers on 2011-10-02
Sadly, no.
The free space is within an extended partition and in between two logical partitions. The XP partition cannot use that as it is.
You now need to move sda5 to the right (by allocating all the free space to the front of that partition (in the first box in the move/resize window in gparted) then shrink the extended partition to match (sda2).
At that point the free space will be outside the extended partition and usable by XP.

---

### Post by sammya on 2011-10-02
> **Quackers said:**
> Sadly, no.
The free space is within an extended partition and in between two logical partitions. The XP partition cannot use that as it is.
You now need to move sda5 to the right (by allocating all the free space to the front of that partition (in the first box in the move/resize window in gparted) then shrink the extended partition to match (sda2).
At that point the free space will be outside the extended partition and usable by XP.

Okay will do that now. Do you recommend any types of software that is reliable enough to merge once I have done everything you told me? In ubuntu and windows?

Cheers

---

### Post by Quackers on 2011-10-02
To be honest it's that long since I used XP (and from what I can remember it doesn't have that facility) I suspect that gparted may be the best option.
From memory I believe I used to use gparted for that kind of thing when I used XP.
Be aware though that moving a Windows partition can cause booting problems.
I would backup anything that you need first, to be sure.

---

### Post by westie457 on 2011-10-02
As Quackers has already stated in post #4 'when the unallocated space is outside of the extended partition then the XP partition can be resized to take in the unallocated space'

These is however two things Quackers did not mention. They are firstly SWAP must be unmounted (in Gparted right-click the SWAP and select 'Swapoff') and secondly whether the XP partition is resized in Windows or using Gparted the next time you boot into Windows there will be a CHKDSK automatically called. LET IT RUN.

---

### Post by Quackers on 2011-10-02
Quite right Westie457. In fact gparted probably won't let you move sda5 unless swap is turned off, as the extended partition may be locked.
Always good practice to turn off swap.

---

