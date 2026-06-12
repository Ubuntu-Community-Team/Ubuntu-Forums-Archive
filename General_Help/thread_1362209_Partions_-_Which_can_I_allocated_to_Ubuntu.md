---
title: "Partions - Which can I allocated to Ubuntu?"
date: 2009-12-22
forum: General Help
---

### Post by vhenry on 2009-12-22
I haven't a clue how, but gparted reports 3 unallocated partitions, in addition to some questionable settings. I thought I had 4: windows, ubuntu 9.10, ubuntu swap and windows/toshiba recovery.

First, if I just need ubuntu and windows (for the time being), which can I delete and second, how do I allocate those unallocated partitions to ubuntu?

---

### Post by dcstar on 2009-12-22
> **vhenry said:**
> I haven't a clue how, but gparted reports 3 unallocated partitions, in addition to some questionable settings. I thought I had 4: windows, ubuntu 9.10, ubuntu swap and windows/toshiba recovery.

First, if I just need ubuntu and windows (for the time being), which can I delete and second, how do I allocate those unallocated partitions to ubuntu?

Do not touch any of those main partitions, you have space in the Extended Partition if you need it.

---

### Post by raymondh on 2009-12-22
> **vhenry said:**
> I haven't a clue how, but gparted reports 3 unallocated partitions, in addition to some questionable settings. I thought I had 4: windows, ubuntu 9.10, ubuntu swap and windows/toshiba recovery.

First, if I just need ubuntu and windows (for the time being), which can I delete and second, how do I allocate those unallocated partitions to ubuntu?

You have 3 primary partitions - all housing windows and recovery.... and 1 Extended partition (which currently houses 2 logical partitions) which is your linux install.

Those small unallocated spaces are probably due to the GB vs. Gib (1 = 1024, binary definition of OS' where 1KB = 1024mb and so on) and when you 'round to cylinder'.

You can use gparted from the liveCD and resize. If you choose to unselect the 'round-to-cylinder' box, you run the risk of having partitions NOT END WITHIN THE CYLINDER BOUNDERIES.  Your call.

Regards,

---

### Post by vhenry on 2009-12-23
It appears that the unallocated spaces are spread out on different parts of the disk (unless I'm misinterpreting), will gparted allow me to specify those spaces only to fold into my primary linux partition?

Am I at serious risk for screwing something up here?

---

### Post by dcstar on 2009-12-23
> **vhenry said:**
> It appears that the unallocated spaces are spread out on different parts of the disk (unless I'm misinterpreting), will gparted allow me to specify those spaces only to fold into my primary linux partition?

Am I at serious risk for screwing something up here?

They are trivial, **do not touch them** as the other things on your laptop may depend on them.

Do you really want to risk wrecking your laptop for an additional 0.01% more disk space?

---

### Post by vhenry on 2009-12-23
That's what I was asking. If they may harm something else, I'll gladly leave the smaller partitions alone (though I'm curious how they got there in the first place), but would like to grab that 81.90 partiton, if its sitting there wasted...

do you think its ok to resize the primary linux partition to add that one?

---

### Post by raymondh on 2009-12-23
> **vhenry said:**
> That's what I was asking. If they may harm something else, I'll gladly leave the smaller partitions alone (though I'm curious how they got there in the first place), but would like to grab that 81.90 partiton, if its sitting there wasted...

do you think its ok to resize the primary linux partition to add that one?

1.  They are there because the partition sizes are 'rounded to cylinders' thus ensuring that each partition reside within a cylinder boundary.

This is my disk:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
[COLOR="Red"]Units = cylinders of 16065 * 512 = 8225280 bytes[/COLOR]
Disk identifier: 0xb1080654

Note the multiplier which I've highlighted in red.

2.  It is ok to resize linux sda5 and enlarge it to occupy the unallocated space (81gb) beside it.

-  Use gparted from the livecd and in live session
-  click to highlight sda5.  With your mouse, grab the right border and drag all the way to the right to occupy the the unallocated.

[HERE'S THE LINK FOR YOUR REFERENC]("http://gparted.sourceforge.net/larry/resize/resizing.htm")E

As always, have a working/tested back-up first.

---

### Post by vhenry on 2009-12-23
thanks Raymond, that explanation makes perfect sense now. will just try to grab that unallocated space next to primary.

Thanks!

---

### Post by raymondh on 2009-12-23
> **vhenry said:**
> thanks Raymond, that explanation makes perfect sense now. will just try to grab that unallocated space next to primary.

Thanks!

Vhenry ...  you're welcome.

If you have a spare machine, you can try to install ubuntu and then resize a partition with the 'round-to-cylinder' box unchecked.  Have fun experimenting.

Also, so as to be clear, your ubuntu install is on sda5 which is a LOGICAL partition, not a PRIMARY.  Do not touch any primary partition unless you want to mess/resize your windows OS or its' recovery partition.

Happy ubuntu-ing.

---

### Post by vhenry on 2009-12-23
logical vs. primary, got it and thanks again. I do have a spare to play around with. funny how we spend our spare time, isn't it? :P

---

