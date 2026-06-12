---
title: "Need help with TestDisk"
date: 2009-07-16
forum: General Help
---

### Post by felinoel on 2009-07-16
I set up the correct partition for to be booted from, and it came up with an error from the operating system, if that fixable? If not, I could resize the partition so it has only enough room for the data in it, and then install the windows and linux in the empty spaces, then later drag the data from the messed up partition, right?
Also, what does this lba flag mean?




For information as to the cause of my problem, see here...
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1214570](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1214570)

[quote="Original Post"][SIZE="1"]I am here with TestDisk, and am unsure what to do from here? I want to un-unallocate a partition?

[http://img123.imageshack.us/img123/4012/screenshotn.png](http://img123.imageshack.us/img123/4012/screenshotn.png)[/SIZE][/quote]

---

### Post by felinoel on 2009-07-16
...

---

### Post by zeronothing on 2009-07-16
if you need to do some partition editing try installing the gparted package using synaptic. I use this to do resizing of hard drives.

---

### Post by starcraft.man on 2009-07-16
Your in luck. [Presto]("http://ubuntuforums.org/showthread.php?t=1200149&highlight=test+disk+starcraft")!

I did a write up a while ago on just using test disk. Scroll down until the very large post by me, follow it. I need to make a guide for this, dunno why but lots of people have been having such hard drive issues and needing test disk lately. That will allow you to recreate your table, assuming there's stuff to salvage.

---

### Post by felinoel on 2009-07-17
> **zeronothing said:**
> if you need to do some partition editing try installing the gparted package using synaptic. I use this to do resizing of hard drives.Hmmm, I will try this if TestDisk doesn't work one more time...

> **starcraft.man said:**
> Your in luck. [Presto]("http://ubuntuforums.org/showthread.php?t=1200149&highlight=test+disk+starcraft")!

I did a write up a while ago on just using test disk. Scroll down until the very large post by me, follow it. I need to make a guide for this, dunno why but lots of people have been having such hard drive issues and needing test disk lately. That will allow you to recreate your table, assuming there's stuff to salvage.Will definitely check this out, thanks

---

### Post by felinoel on 2009-07-17
> **zeronothing said:**
> if you need to do some partition editing try installing the gparted package using synaptic. I use this to do resizing of hard drives.

Wait, gparted is what caused my problem in the first place?

---

### Post by felinoel on 2009-07-17
How do I move the keys in gparted from one partition to another? What does the lba flag mean?

---

### Post by felinoel on 2009-07-17
I am going to guess those keys mean which partition you are using, I set up the correct partition for to be booted from, and it came up with an error from the operating system, if that fixable?


If not, I could resize the partition so it has only enough room for the data in it, and then install the windows and linux in the empty spaces, then later drag the data from the messed up partition, right?

---

### Post by felinoel on 2009-07-17
...

---

### Post by felinoel on 2009-07-17
...

---

### Post by zeronothing on 2009-07-17
I'm not sure I understand what the "Keys" are. Are you trying to create a partition that is bootable? If that is the case, their are flags you need to set for the new partition you created in order to boot from that partition. I just need a little more incite into what your trying to accomplish.

---

