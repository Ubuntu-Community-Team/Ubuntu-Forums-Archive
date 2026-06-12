---
title: "Recovering data-a sad saga of data loss"
date: 2010-02-20
forum: General Help
---

### Post by jsriz on 2010-02-20
[COLOR=Sienna]I Know that it is too ambitious for me to even ask this :[/COLOR]
I was trying to test some softwares that claimed to mount ext4 file system  in windows7 (The Most Stupidest Thing I Have Done In A Lifetime)

After sum unsuccessful efforts (which showed a disk in my computer which  did not open) and a reboot i got a blank screen with what i remember to  be some grub error.
being impatient i instantly booted up a live cd and it didn't show any  harddisk that could be mounted
being a noob to terminal at that time and being extremely impatient  again i decided to go the hard way (without remembering about some  important n personal files that where there on my windows partition) -
Reinstalll everything from windows7 to ubuntu.
after few days realizing that windows sucked before the options that  linux gave i decided to make a fresh install a dual boot of Ubuntu n  Opensuse which i have been using till date.
But now after some random surfing i found that data recovery is possible  unless a file shred was done.
Would it be by sum means possible to recover files to even sum extent.I  promise to do any amt of reading.
Also would like to know what i shed have done when my hard disk was not  accessible.

---

### Post by jsriz on 2010-02-21
bump

---

### Post by jenaniston on 2010-02-21
> **jsriz said:**
>  (The Most Stupidest Thing I Have Done In A Lifetime)

. . .some  important n personal files that where there on my windows partition) -
. . . i decided to make a fresh install a dual boot of Ubuntu n  Opensuse which i have been using till date.
But now after some random surfing i found that data recovery is possible  unless a file shred was done.

Would it be by sum means possible to recover files to even sum extent.

Also would like to know what i shed have done when my hard disk was not  accessible.

In general, there is no really good reason (usually) for a full install at first with all the live versions - but anyway . . .

All with a live version - not a full install . . . 
linux can read, access, move, open, - even take deleted files out of a Windows partition - whether fat or ntfs.

It sounds like you may have overwrote the Windows partition if I understand you correct . . .
or is the physical layer space where the Windows filesystem was (and hopefully still is) there
and just "unrecognized" so yet possibly recoverable ? Any other details ?

what does 
```
sfdisk -l
```look like ? listing the partitions only then exits - so no changes btw.

---

