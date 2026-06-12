---
title: "ext2 vs. ext3/4"
date: 2011-09-29
forum: General Help
---

### Post by steevven1 on 2011-09-29
I want to install Ubuntu on an ext2 file system. I'm not really interested in debating whether or not I should do this, but I'd like to know what differences I might encounter vs. ext4, which I have always used. Speed? Reliability? Anything else at all?

How will its being a non-journaling file system affect me?

Thanks a lot!

---

### Post by blueridgedog on 2011-09-29
This may help:

[http://www.thegeekstuff.com/2011/05/ext2-ext3-ext4/](http://www.thegeekstuff.com/2011/05/ext2-ext3-ext4/)

I use ext2 on my systems that boot and run off of non traditional disk media (flash drives and the like).

---

### Post by FormatSeize on 2011-09-29
> **steevven1 said:**
> I'd like to know what differences I might encounter vs. ext4, which I have always used. Speed? Reliability? Anything else at all?
 
How will its being a non-journaling file system affect me?
I don't think you will encounter much of anything. The filesystem itself isn't really something that substantially affects the general things that the user does. 
 
I've tried Ext2, Ext3, Ext4, and BTRFS, and I didn't notice anything handling differently between them. Perhaps, though, I'm simply not, or don't know how to do things where the filesystem becomes noticeable.

---

