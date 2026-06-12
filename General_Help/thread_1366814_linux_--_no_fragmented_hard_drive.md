---
title: "linux -- no fragmented hard drive ??"
date: 2009-12-28
forum: General Help
---

### Post by oospill on 2009-12-28
I've been using Linux for about 8 months now, and I just got to wondering.. why is there no way do defrag my HD?  I read once that Linux doesn't need it.  Could someone explain this to me, or better yet, forward me to a website that explains??

thanks!!
oospill

---

### Post by dcstar on 2009-12-28
> **oospill said:**
> I've been using Linux for about 8 months now, and I just got to wondering.. why is there no way do defrag my HD?  I read once that Linux doesn't need it.  Could someone explain this to me, or better yet, forward me to a website that explains??


This has been discussed many times in the forums, do a search for them.

---

### Post by warfacegod on 2009-12-28
I can't find the documentation at the moment, sorry. This is something I Looked into about two years and it just isn't needed. Although, I think the servers use some minor form of it. If I were you, I'd smile and never think about it again. Like I did.

---

### Post by KiLaHuRtZ on 2009-12-28
> Defragmentation

There is no online ext3 defragmentation tool that works on the filesystem level. An offline ext2 defragmenter, e2defrag, exists but requires that the ext3 filesystem be converted back to ext2 first. But depending on the feature bits turned on in the filesystem, e2defrag may destroy data; it does not know how to treat many of the newer ext3 features.[14]

There are userspace defragmentation tools like Shake[15] and defrag.[16][17] Shake works by allocating space for the whole file as one operation, which will generally cause the allocator to find contiguous disk space. It also tries to write files used at the same time next to each other. Defrag works by copying each file over itself. However they only work if the filesystem is reasonably empty. A true defragmentation tool does not exist for ext3.[18]

That being said, as the Linux System Administrator Guide states, "Modern Linux filesystem(s) keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system."[19]

While ext3 is more resistant to file fragmentation than the FAT filesystem, nonetheless ext3 filesystems can get fragmented over time or on specific usage patterns, like slowly-writing large files.[20][21] Consequently the successor to the ext3 filesystem, ext4, includes a filesystem defragmentation utility and support for extents (contiguous file regions).

[http://en.wikipedia.org/wiki/Ext3#Defragmentation]("http://en.wikipedia.org/wiki/Ext3#Defragmentation")

---

### Post by howefield on 2009-12-30
Here is another link, this has a simple diagram explanation.

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

