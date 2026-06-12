---
title: "Shriking Ubuntu partition and Extending Windows Partition help?"
date: 2011-08-04
forum: General Help
---

### Post by georgeos on 2011-08-04
So I dual booted Ubuntu with Windows 7 as I usually do with a fresh hard drive, but this time I gave Windows a little less space than I should have, only 40gb, and ubuntu 560, but now I don't have enough room for my wine incompatible windows apps. A while back I was going to do something similar but I was warned about data loss, or the bootloader getting messed up, so I just reistalled both OSs seeing as it was a fresh hard drive, but i've been using this set up for around 2 months now, and all data is on. So my question is, what is the safest way to shrink the Ubuntu partition and extend the Win7 one.

Thanks

GH

---

### Post by flemur13013 on 2011-08-04
I'm assuming you only have two partitions.

Boot from the ubuntu install CD and use gparted to shrink the ubuntu (ext3/4) partition.

In windows you can grow your C: partition while using it with "Easeus Partition Master" or "Partition Wizard" (both free from download.com) or whatever primitive tools windows provides.

- or - 

Come to think of it and IIRC, one or both the above can handle ext3/4 partitions as well as NTFS (if not, it's "Paragon Partition Mgr" - there's a free edition, not sure about it and ext3/4 partitions), so you can do it all while running windows normally.   They can expand your windows partition while windows is running, but need to reboot to shrink it, and (the right one(s)) can shrink ext3/4 partitions, also while windows is running.

Edit: Boot windows, run the right partitioning program (!!), shrink the ext3/4 partition, then grow the windows partition into the free space. When you shrink, make the freespace be next to the windows partition!

---

### Post by georgeos on 2011-08-05
> **flemur13013 said:**
> I'm assuming you only have two partitions.

Boot from the ubuntu install CD and use gparted to shrink the ubuntu (ext3/4) partition.

In windows you can grow your C: partition while using it with "Easeus Partition Master" or "Partition Wizard" (both free from download.com) or whatever primitive tools windows provides.

- or - 

Come to think of it and IIRC, one or both the above can handle ext3/4 partitions as well as NTFS (if not, it's "Paragon Partition Mgr" - there's a free edition, not sure about it and ext3/4 partitions), so you can do it all while running windows normally.   They can expand your windows partition while windows is running, but need to reboot to shrink it, and (the right one(s)) can shrink ext3/4 partitions, also while windows is running.

Edit: Boot windows, run the right partitioning program (!!), shrink the ext3/4 partition, then grow the windows partition into the free space. When you shrink, make the freespace be next to the windows partition!

So I booted into GParted, and shrunk my Ubuntu partition by 100gb today,   in the hopes that I would be able to extend my Windows partition.   However GParted won't let me extend this unallocated space into my   Windows partition. I booted into Windows, and still no luck, I tried   EASEUS partition manager, which didn't work.  So I shrunk my current  Windows partition (within windows) by about 1gig  to check if I could re  extend it. And what I found was that the new  unallocated space seemed  to be separate from the 100gb unallocated  space, they wouldn't merge.  But I was able to re extend that 1gig back  to the Windows partition.
But I'll give Paragon a try

Thanks

---

### Post by Furball588 on 2011-08-05
I'm pretty sure you're going to need to move ubuntu around, so your unpartitioned space is after your windows partition.

---

### Post by georgeos on 2011-08-05
> **Furball588 said:**
> I'm pretty sure you're going to need to move ubuntu around, so your unpartitioned space is after your windows partition.

How?

---

### Post by flemur13013 on 2011-08-05
**Post a screen-shot of what your disk layout looks like!*  **(either from gparted or palimpsest ("disk utility") in linux, or from whatever in windows). 

I gather you have some 100g free space created with gparted, but can't extend the C: partition into it.
Easeus didn't work? What did it do? Or not do?  (Easeus is VERY similar to Partition Wizard).

If you have the free space next to windows partition any of the pgms should be able to extend the C: part into the free space.  You *should* be able to do the rest of the process in Windows.

Paragon Enterprise (v 8.0) and Partition Wizard (v 5.0) can do ext3 (and linux swap) but apparently **not ext4** (unless newer versions can), but maybe you're done with the Linux side (creating the free space).

*Or send your screen-shot to my email:  "flemur13013 AT gmail.com" (remove the spaces and replace "AT" with @)  I've done what you're trying to do - several times!- but it was a while  ago and I'm not dual-booting anymore, just XP under virtualbox now, so I  can't really emulate what you're trying to do.

---

### Post by Furball588 on 2011-08-05
> **georgeos said:**
> How?

I'd have to see why you're looking at too.  I'm like flemur...done it a 100 times, but now don't have it setup like this to properly do the way you would...Unfortunately, this isn't something that can be done in one fell swoop.

I guess the way I'm imaging things you would shrink whatever /home is and move that to the right...then move / to the right and your swap to the right... :)  Again...will probably take multiple steps..

---

### Post by dBuster on 2011-08-05
Either way you try to shrink or expand partitions you can not do it while using an operating system in said particular partition.  

So the best way to do it is to boot from a live cd of some sorts.  There are several good partition programs out there some with a 30 day FREE trial in which you create a boot disk/usb stick and then you can modify your partitions all you want.

I too had a similar issue with my windows partition and it was a bear to work with but it can be done.  What program did I use, I can't remember now as I am at work and at home now there are no windows machines what so ever...  Purely linux and Ubuntu only!

---

### Post by flemur13013 on 2011-08-05
> **dBuster said:**
> Either way you try to shrink or expand partitions you can not do it while using an operating system in said particular partition.  

You can expand/grow an NTFS partition into free space while using it, e.g. the C: partition; I've done it several times (tho there may be circumstances when a reboot is needed -?). For shrinking or moving, the pgms I mentioned will set up a script to run at reboot. I've done just about everything you can do with (or to!) NTFS partitions under XP and Win7, and never had to boot from a CD. (I didn't like the MFT wasting so much space and did partition sizing tricks to shrink it.)

---

