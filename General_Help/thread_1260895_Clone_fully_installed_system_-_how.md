---
title: "Clone fully installed system - how?"
date: 2009-09-08
forum: General Help
---

### Post by Thanh-BKK on 2009-09-08
Hi.

I have Ubuntu 9.04 Jaunty and now i wish to do two things:

1) Get it "as is" on a second computer (SMALLER hard disk!) and
2) Take a full backup on an identical second hard disk

The system is on a 120 GB hard disk, of which 40 GB is /home, 36 GB is / and 4 GB is SWAP. Obviously not all the space is used, in fact only about 20 GB of /home (including several virtual machines) and a few GB of / so it should be possible to get all of that onto an 80 GB hard disk (second computer). 

The backup will be on a second HDD identical to the one in the computer.

The way i want to do it is to hook up either HDD to the machine via USB/external enclosure, clone the internal disk respectively copy ALL it's data, then put the 80 GB disk in the second computer and have it work and keep the second HDD as a backup.

Both HDD's must be straight bootable, i.e. i do not want to have to fiddle around with reinstalling Grub and similar procedures.

Basically what i need is a bit-for-bit copy of the internal drive. 

So how can i do that? Preferably from within the booted system and with GUI. 

I appreciate any help on the subject... many thanks in advance.

Kind regards.....

Thanh

---

### Post by P4man on 2009-09-08
Hmm.. dd could do all that, but not to a smaller disk.

I'd suggest you run partition editor from a live cd, and shrink your current partitions to the point where they would fit on the 80GB drive. keep the rest unallocated,then you can use dd or if you prefer gui, clonezilla:

[http://clonezilla.org/](http://clonezilla.org/)

After that, grow the partition again.

If your external hdd is big enough to hold all 120HV, clone to that external disk first, then shrink the partition on it. That way you have a backup before doing the resizing, which is usually a good idea :)

The cloned install should work btw, provided they have similar graphic cards (or if you didnt install any proprietary drivers).

---

### Post by rob-ward on 2009-09-08
Rather than shrinking the partitions on the drive that is running(you can risk data loss) I would copy the partitions one by one using dd to the new drive and then resize them on the new drive, that way if anything goes wrong you still have the original.

---

### Post by Thanh-BKK on 2009-09-09
Hi.

I think i found a fool-proof way - since Ubuntu installs almost ridiculously fast, i simply hooked up the smaller drive in the second computer, installed Jaunty from scratch, got all my packages from the first computer via AptOnCD, all contents of /home via another USB hard disk and after about an hour altogether (!) i was all set and ready to roll. 

I think even DD would not have done it much faster :)

And with the second 120 GB HDD i think i will do exactly the same.

Kind regards.....

Thanh

---

