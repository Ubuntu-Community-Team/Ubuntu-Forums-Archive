---
title: "Having trouble merging partitions"
date: 2009-08-22
forum: General Help
---

### Post by foogoo on 2009-08-22
I previously had a dual-boot setup with Vista, so my HD partitions looked something like:

Vista - Ubuntu - Swap

Today I deleted the Vista partition so it is now unallocated space. I want to merge that unallocated space with the Ubuntu partition. I've tried Gparted (through System Rescue CD) and the partition tool on the Mandriva live CD but neither would let me move the partitions or resize the Ubuntu partition to absorb the unallocated space. What should I try now?

---

### Post by P4man on 2009-08-22
the ubuntu and swap partitions are likely contained inside an extended partition. What you have to do is boot from the live cd as you did, run gparted. Then swapp off the swap (right click it and select swap off). Then you should be able to grow the extended (light blue) partition first. After that, you can grow the other partitions inside the extended. 

However Im not entirely sure its a good idea to only have 1 extended partition and the rest inside that. perhaps someone else can elaborate or reassure us its ok.

---

### Post by serpantman on 2009-08-22
Why does the swap have to be turned off in order to resize the partition?

---

### Post by oboedad55 on 2009-08-22
> **serpantman said:**
> Why does the swap have to be turned off in order to resize the partition?

It doesn't, it's not mounted.

---

### Post by P4man on 2009-08-22
yes it does, a live cd will always swap on any existing swap partitions it finds. That means its mounted, and you can't resize an extended partition if partitions inside it are mounted.

---

### Post by oboedad55 on 2009-08-22
> **P4man said:**
> yes it does, a live cd will always swap on any existing swap partitions it finds. That means its mounted, and you can't resize an extended partition if partitions inside it are mounted.

Okay, thanks for the info. I stand corrected! :P

Jon

---

### Post by drs305 on 2009-08-22
foogoo,

@ P4man - Yes, having only an extended partition does seem a bit odd but it will work. However, I would leave at least one (other) primary partition regardless, even if it was empty. And of course, if Windows were ever to be restored, it would need to go in a primary partition (or VM).

I wrote a guide about taking space from Windows to put into Linux. Although your circumstances vary a bit, the principles are the same (unmount, expand the extended partition first, then expand Ubuntu). Here is the link:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by foogoo on 2009-08-22
Thanks for the replies, I will give the suggestions a shot today.

Can someone elaborate on why it is odd to have only an extended partition? I want to convert this system from dual-boot to Ubuntu only. What would you suggest instead? That I format the unallocated space and leave it be?

---

### Post by P4man on 2009-08-22
Usually an extended partition is used to get around the limitation of 4 primary partitions per drive. But I guess there is no real problem. In fact one might wonder why not always make the entire drive 1 extended partition. Probably windows doesn't like it? dont know...

---

