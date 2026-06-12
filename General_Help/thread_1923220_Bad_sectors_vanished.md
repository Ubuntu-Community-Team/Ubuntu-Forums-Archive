---
title: "Bad sectors vanished?"
date: 2012-02-10
forum: General Help
---

### Post by kanishkdudeja on 2012-02-10
I had some problems copying files from a partition..some files could'ne be copied..it said input/output error..

i opened gparted partition editor..

and there it was written that there are atleast 3 bad sectors on this drive..

i recovered most of the data from this partition..and then i formatted it..

now gparted does'nt inform me of any bad sectors..

Have the bad sectors vanished or are they still there and i need to do something about them?

---

### Post by 2F4U on 2012-02-10
I would guess that either gparted or the hdd marked the sectors as bad and thats why you don't see them again. They didn't go away but the OS doesn't touch them since they are marked as bad. If new sectors arise, you would get the same problems again.

---

### Post by Grenage on 2012-02-10
If it's only a few bad sectors, and that number doesn't start increasing, you don't need to worry about it.  Hard drives automatically 'quarantine' known bad sectors, so the system works around them.

That said, when a hard drive starts to generate bad sectors it can be down to failing hardware.  Those tend to be rather obvious, as the sector count increases and you'll get strange errors or system crashes.

Suck it and see, but always keep your important data backed up.

---

### Post by Gremlinzzz on 2012-02-10
What Causes Bad Sectors?:popcorn:
[http://www.ehow.com/info_8340033_causes-bad-sectors.html](http://www.ehow.com/info_8340033_causes-bad-sectors.html)

---

### Post by kanishkdudeja on 2012-02-13
Thanks all for your opinion.

Well, i ran a SMART Test in Disk Utility.

It showed 577 bad sectors but that number hasn't been increasing since then.

Now the partition which had bad sectors, I've deleted that partition so that the bad sectors don't increase.

I checked the remaining partitions with chkdsk.

It showed no bad sectors.

Is there any utility for Linux which can check for bad sectors in a partition so that i can periodically check my partitions for bad sectors?

---

### Post by Grenage on 2012-02-13
> **kanishkdudeja said:**
> Is there any utility for Linux which can check for bad sectors in a partition so that i can periodically check my partitions for bad sectors?

Smart will generally take care of this for you, and I believe Ubuntu checks SMART (I recall false positives some time ago).

---

### Post by 3rdalbum on 2012-02-13
> **kanishkdudeja said:**
> Thanks all for your opinion.

Well, i ran a SMART Test in Disk Utility.

It showed 577 bad sectors but that number hasn't been increasing since then.

Now the partition which had bad sectors, I've deleted that partition so that the bad sectors don't increase.

I checked the remaining partitions with chkdsk.

It showed no bad sectors.

Is there any utility for Linux which can check for bad sectors in a partition so that i can periodically check my partitions for bad sectors?

577 bad sectors sounds like a lot. If you have deleted the partition that all those sectors were spread across, then the disk will never read that partition and never see any more bad sectors in that area.

Just keep an eye on Disk Utility. If the disk detects any more bad sectors, then Disk Utility will display the number as higher. But the disk won't detect any more bad sectors until they start creeping into space that you are using.

---

### Post by kanishkdudeja on 2012-02-28
Well, ive purchased a new disk now.

The number of bad sectors was increasing rapidly.

---

