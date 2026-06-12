---
title: "Partition problem"
date: 2009-08-25
forum: General Help
---

### Post by yildiz.a on 2009-08-25
I installed Ubuntu after installing Win XP. And a situation occured that I cannot use -parent- free space over Ubuntu Filesystem. I attached the related screenshot into the page. Any help appreciated. Thanks...

---

### Post by dandnsmith on 2009-08-25
Easiest would be to start over with a new ubuntu installation - that way you could get the space reallocated how you want without undue trouble.

If, however, you have settings you want to keep, you could do something like backup the ubuntu ext3 filesystem to some 'external' storage, delete the extended partition (and the included stuff), create partitions the way you want them, and then restore the backed up content. Then 'all' you have to do is sort out the booting problem which will almost certainly have occurred (as the recreated partitions will have different uuids).

It's possible that someone with a bit more experience in handling these partitions can tell you how to do the resizing, more simply, using gparted from a liveCD (for example)

---

### Post by P4man on 2009-08-25
> **yildiz.a said:**
> I installed Ubuntu after installing Win XP. And a situation occured that I cannot use -parent- free space over Ubuntu Filesystem. I attached the related screenshot into the page. Any help appreciated. Thanks...

Is sda5 where you have ubuntu isntalled, and you want to grow that partition? If so, not that hard.

 Right click sda5 and select "unmount". Right click the swap partition and select "swapoff". Then right click sda2, the blue, extended partition (which acts like a container for sda5 and sda6), and select resize. Make it as big as you want. After that, you can resize sda5 to give ubuntu more space.

Let me know if it works.

---

### Post by yildiz.a on 2009-09-02
> **P4man said:**
> Is sda5 where you have ubuntu isntalled, and you want to grow that partition? If so, not that hard.

 Right click sda5 and select "unmount". Right click the swap partition and select "swapoff". Then right click sda2, the blue, extended partition (which acts like a container for sda5 and sda6), and select resize. Make it as big as you want. After that, you can resize sda5 to give ubuntu more space.

Let me know if it works.


Thank you, it was so easy. It worked.

---

### Post by peteair1 on 2009-09-02
P4man...Does the unallocated space need to be formatted prior to re-sizing the extended partition? I just tried this yesterday and ended up with a mess. I took 30gig off a ntfs, and extended the extended partition by 30gig, then re-sized my root 30gig. My original root was 9gig+ with used 5gig+, now gpart shows root 39gig+ with 35gig+ used, Where did I go wrong and can it be fixed? Here is a screen-cap.

---

### Post by P4man on 2009-09-02
> **peteair1 said:**
> P4man...Does the unallocated space need to be formatted prior to re-sizing the extended partition? 

No. On the contrary. It must remain unallocated. You can only grow a partition "into" unallocated space.

> I just tried this yesterday and ended up with a mess. I took 30gig off a ntfs, and extended the extended partition by 30gig, then re-sized my root 30gig. My original root was 9gig+ with used 5gig+, now gpart shows root 39gig+ with 35gig+ used, Where did I go wrong and can it be fixed? Here is a screen-cap.

Thats odd.. did you resize from a liveCD?
Either way, see what uses up all that space: applications > accessories > Disk usage analyser.

---

### Post by peteair1 on 2009-09-02
Yes I used Ubuntu 8.10 Live Disc/gpart

---

### Post by peteair1 on 2009-09-02
P4man, Kdiskfree shows it unchanged.

---

### Post by P4man on 2009-09-02
hmm, something must be wrong there :)
boot the live cd again, and check the partition for errors.

---

### Post by peteair1 on 2009-09-02
P4man....It gets weirder ....Last night I booted the live disc and did the check/repair on that partition and it said it could not repair..Just did it again, and it gave me a green check..repaired. Rebooted back to Kubuntu/gpart and it is in fact repaired and as it should be. Thanks for telling me to do it again..:popcorn:

---

### Post by P4man on 2009-09-02
IIRC, if you change anything to partitions, you need a reboot for ubuntu to see the changes properly. Not that that quite explains why you saw, but if its all working now, then so much the better :)

---

