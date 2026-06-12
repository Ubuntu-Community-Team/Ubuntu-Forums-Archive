---
title: "I have 2 SWAP paritions - that a problem?"
date: 2012-05-26
forum: General Help
---

### Post by listerdl on 2012-05-26
I had a bit of a crisis following a kernel panic and long story short I had to wipe my drive and re-partition using gparted.

Anyways it all went well - and I set up my dual boot just the way I like it....

However - I notice that somehow I have created 2 x 2GIG Linux Swap Paritions....

Is that an issue or just a waste of 2 gig?

Can I safely delete either of those or do you think I will be entering a world of pain?

---

### Post by malspa on 2012-05-26
You don't need two, but I've had two swap partitions (one on each hard drive) with no problem. I've never had two on the same hard drive, though.

---

### Post by hangfire on 2012-05-26
As Malspa said, Linux has no issue with multiple swap partitions, on one device or several. If they are not being used, you can turn them off dynamically with the swapoff command (and sudo of course).

To repartition it is best to boot from optical or USB media and use a tool like gparted to delete and resize partitions.

HF

---

### Post by fantab on 2012-05-26
I don't think it is an issue to have two SWAP partitions. Unless you badly need that 2gb of space of additional SWAP, I would suggest let it be. In future when you reinstall your Ubuntu to upgrade then you can delete it and merge the space elsewhere.

---

### Post by listerdl on 2012-05-27
thanks for all replies.

Ill probably just let it be but out of interest how would I know which one is being used?

I gave command "free" in a terminal and it gave info about the size of my SWAP partition - I guess that would be a simple method....

Also, slightly off topic but is there *really* any point in SWAP? I have 4 gig RAM on a laptop and I dont run huge resource programs and I never hibernate...

Why do we bother?

---

### Post by malspa on 2012-05-27
To see which one is being used:

```
# swapon -s
```

Also, see **man swapon**.

To see info on all partitions:

```
# fdisk -l
```

> **listerdl said:**
> Also, slightly off topic but is there *really* any point in SWAP? I have 4 gig RAM on a laptop and I dont run huge resource programs and I never hibernate...

Why do we bother?

With that much RAM, and never using hibernate, good question...

---

### Post by listerdl on 2012-05-27
> **malspa said:**
> With that much RAM, and never using hibernate, good question... Yeah - why bother?

Maybe SWAP is a hang-up from the past....

Thanks for your help above...

---

