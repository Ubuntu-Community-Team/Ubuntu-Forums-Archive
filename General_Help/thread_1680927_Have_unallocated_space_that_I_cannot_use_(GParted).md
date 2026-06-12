---
title: "Have unallocated space that I cannot use (GParted)"
date: 2011-02-03
forum: General Help
---

### Post by christatedavies on 2011-02-03
Hello. I used to run Windows and Ubuntu side by side. I have removed Windows and only run Linux now.

However, when I try to release the partitions for use with Linux, Gparted just doesn't give me the correct resize options.

Have attached a file, so you can see my problem.

I believe its because the /dev/sda4 drive is sandwiched between the two unallocated partitions, and I just have no option of resizing into those empty ones. I have tried formatting them, but it just won't play.

Ignore the fact they have locked keys, I have been using the Live CD to boot, but this screenshot was taken from my normal login.

Thanks, Chris

---

### Post by psusi on 2011-02-03
It looks like sda2 is the windows boot partition, so you can blow that away as well.  sda5 and 6 are logical partitions that exist within the sda4 extended partition, so to expand them, you must first expand the extended partition.

---

### Post by christatedavies on 2011-02-03
> **psusi said:**
> It looks like sda2 is the windows boot partition, so you can blow that away as well.  sda5 and 6 are logical partitions that exist within the sda4 extended partition, so to expand them, you must first expand the extended partition.

It won't let me expand the extended partition. That's the problem. Well, I tell a lie, it will let me resize it, but no bigger than it already is.

It won't let me use the unpartitioned space. Is there a format it should be to let me do so? I tried formatting it as ext4 but it had the same result...

Thanks

---

### Post by psusi on 2011-02-03
> **christatedavies said:**
> It won't let me expand the extended partition. That's the problem. Well, I tell a lie, it will let me resize it, but no bigger than it already is.

Are you sure that you were trying to resize sda2 and not sda5?  Also make sure you don't have any keys icons anywhere, especially the swap partition.  You probably need to unmount that.

> **christatedavies said:**
> It won't let me use the unpartitioned space. Is there a format it should be to let me do so? I tried formatting it as ext4 but it had the same result...


What do you mean?

---

### Post by Elfy on 2011-02-03
> It won't let me expand the extended partition. That's the problem. Well, I tell a lie, it will let me resize it, but no bigger than it already is.First you need to make sure nothing is mounted - in the livecd - right click the swap partition and turn it off.

You might be able to expand it to the left - never tried myself. If you can't expand to the left you need to make sure that any space you want to add to the extended is contiguous.

---

### Post by christatedavies on 2011-02-03
> **psusi said:**
> Are you sure that you were trying to resize sda2 and not sda5?  Also make sure you don't have any keys icons anywhere, especially the swap partition.  You probably need to unmount that.

I did unmount the SWAP partition. There were no keys when I tried to do it from the Live CD.

> What do you mean?

I just meant was there a reason why it won't let me expand my primary partition into the empty space. Should I format it?

Nothing seems to has any effect.

---

### Post by Elfy on 2011-02-03
I think I understand what you are saying now, to resize the sda5 partition you have to resize sda4 first.

---

### Post by christatedavies on 2011-02-03
> **forestpiskie said:**
> I think I understand what you are saying now, to resize the sda5 partition you have to resize sda4 first.

I don't think it will let me resize that either. I will reboot in a minute with the Live CD and let you all know.

Thanks for your help so far.

---

### Post by psusi on 2011-02-03
> **christatedavies said:**
> 
I just meant was there a reason why it won't let me expand my primary partition into the empty space. Should I format it?


Format what?  Did you try to create a new partition or not?

---

### Post by christatedavies on 2011-02-03
> **psusi said:**
> Did you try to create a new partition or not?

Yes I did. Unformatted and formatted as ext4

---

### Post by christatedavies on 2011-02-03
Well, I don't know what's changed. But I just tried all this again and now its working and currently resizing as I type.

Very odd. But thanks guys for your input!

---

