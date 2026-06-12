---
title: "partitioning question"
date: 2009-11-30
forum: General Help
---

### Post by commonplace on 2009-11-30
I wiped out my laptop and installed Windows 7. I told it to make a 40GB partition. Somehow, it stole half of the hard drive. Still not sure how that happened. But I didn't notice until well after I'd already installed Ubuntu 9.10. So I went into Win7 and shrunk the partition to 40GB as I'd wanted to begin with, and went back into Ubuntu and tried to use gparted to grow my Ubuntu partition -- but I don't see how to do it.

Here's a screenshot of my current partitions. Can anyone tell me how to add that "unallocated 115.56GiB" space to my / (/dev/sda5) ext4 partition? Is that possible? Don't mind using third-party tools if I have to, but if gparted can do it, that'd be even better. (I know I'd have to do it from the Live CD.)

Thanks!

/Kevin

[IMG]http://www.envail.com/commonplace-partitions.png[/IMG]

---

### Post by u.b.u.n.t.u on 2009-11-30
The thumbnail size is ok, but the linked screenshot is rather too small to see properly.

There should be an option to expand, resize and even merge partitions. It depends on what software you are using as to how to proceed. I would think however, that such features would be standard fair.

---

### Post by commonplace on 2009-11-30
> **u.b.u.n.t.u said:**
> The thumbnail size is ok, but the linked screenshot is rather too small to see properly.

There should be an option to expand, resize and even merge partitions. It depends on what software you are using as to how to proceed. I would think however, that such features would be standard fair.

I was trying to do it using GParted, but I can't figure out how to do what I want it to do. I think if the free space were to the 'right' of the existing Ubuntu partition, it would let me expand into that space, but it's to the 'left' so it doesn't. Not sure what to do.

/Kevin

---

### Post by u.b.u.n.t.u on 2009-11-30
The following site may be of interest:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Bucky Ball on 2009-11-30
When you are resizing your Ubuntu partition (the one with the OS on it) you MUST do this from either the LiveCD or the Gparted LiveCD as your partition must be UNmounted. This is not possible when you are running the OS from the partition you are trying to resize, for obvious reasons. :)

---

### Post by efflandt on 2009-11-30
You have to select a partition, then you should be able to resize it.  So it you select your Ubutunu partition you should be able to resize it to fill the unallocated space.  But it may take awhile.  And you cannot be running from it at the time.

I have been using gparted-live CD (which should be most recent version) to shrink Windows partitions to make room for Linux.  The resize icon should also be able to expand partitions, especially Linux partitions.

---

### Post by commonplace on 2009-11-30
I'm on the Live CD, but no matter what I do, it doesn't let me do what I want it to do. With my partitions exactly as they are now, I click on /dev/sda5 (my Ubuntu partition) and click on Resize/Move. It shows that it's already as big as it can get. It doesn't let me grow the partition using the 115.56 gigs of unallocated space. Any idea why?

/Kevin

---

### Post by jacobs444 on 2009-11-30
you need to resize the light blue extended(logical) partition to resize the ubuntu one.

you are clicking the ext4 partition, am i right. Click the one above it that says extended.

---

### Post by commonplace on 2009-11-30
> **jacobs444 said:**
> you need to resize the light blue extended(logical) partition to resize the ubuntu one.

you are clicking the ext4 partition, am i right. Click the one above it that says extended.

I was clicking on the ext4 partition itself, as you thought. But when I click on the light blue/extended/logical partition, I don't get ANY options at all. (Aside from 'Manage Flags' and 'Information' -- everything else, including Resize/Move, is grayed out.)

I thought we had it there! It sounded good. hehe  Any other ideas?

I'm downloading the actual GParted Live CD now, to see if it offers any different choices. I'd been trying off the latest Ubuntu 9.10 Live CD, so it's not antiquated or something, but I figure it's worth a try in the meantime.

/Kevin

---

### Post by Bucky Ball on 2009-11-30
Same Gparted if you are going the latest version. Probably won't make any difference and no different options.

---

### Post by commonplace on 2009-11-30
> **Bucky Ball said:**
> Same Gparted if you are going the latest version. Probably won't make any difference and no different options.

Yep, just finished discovering that. *sigh*  I can't figure out why it's not letting me do what I want. Very frustating. Appreciate everyone's help. Hopefully someone figures it out. :)

/Kevin

---

### Post by u.b.u.n.t.u on 2009-12-01
Can you try to reinstall Ubuntu and during the installation set the parameters of the partition?

That may not be as eloquent as combining two partitions but it would at least address the problem.

The other possibility is formatting the partition in question with ext4 and seeing if that resolves the merging.

---

### Post by commonplace on 2009-12-01
> **u.b.u.n.t.u said:**
> Can you try to reinstall Ubuntu and during the installation set the parameters of the partition?

That may not be as eloquent as combining two partitions but it would at least address the problem.

The other possibility is formatting the partition in question with ext4 and seeing if that resolves the merging.

I tried your latter suggestion of formatting the partition as ext4, but that didn't help.

In the end, I'm probably just going to do nothing. When the next version of Ubuntu comes out (hey, it's only 4.5 months away), I'll just wipe the Linux partitions out and redo 'em then. Thank you all for your help!

/Kevin

---

### Post by u.b.u.n.t.u on 2009-12-01
Alpha 1 of Lucid Lynx is scheduled for 10 December. That may be worth taking a look at out of interest.

[https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule)

Ubuntu 9.10 is being updated regularly so the wait may not be that long.

---

### Post by NorthDakota91 on 2010-03-19
I had the same problem until..now ^^. I found why GParted from the Ubuntu LiveCD couldn't resize the ext4 partition. This happened because the live CD used the swap partition on hard drive. So all you have to do is just right click on the swap partition and "swapoff". After that you'll be able to resize, move, etc..

Hope this helped!

---

