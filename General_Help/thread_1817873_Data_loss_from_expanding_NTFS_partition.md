---
title: "Data loss from expanding NTFS partition?"
date: 2011-08-03
forum: General Help
---

### Post by Buuntu on 2011-08-03
This forum might not be the best place for this question, but some people here are pretty knowledgeable and may have more insight than I do about this.  
Anyways, I'm thinking about expanding an NTFS (Windows 7) partition on my desktop computer into unallocated space.  I know that there is a risk when shrinking a NTFS partition due to fragmentation but are there any risks of data loss from expanding a NTFS partition?  My common sense tells me there isn't a risk but I want to be 100% sure I won't lose any files.

---

### Post by jwbrase on 2011-08-03
There's always a risk when doing *any* work on *any* partition. It's always a good idea to make a backup before repartitioning. The risk isn't huge but it is there.

---

### Post by Buuntu on 2011-08-04
Alright that's not helpful...  I realize that there's risk in everything but is it relatively safe to expand a NTFS partition or not?

---

### Post by Mark Phelps on 2011-08-04
The posts we've seen about data corruption from using GParted (or the Ubuntu installer) on Win7 OS partitions have been about shrinking it.  Not seen any about expanding it.

But, why take the risk?  If it fails, you end up with an unbootable Win7 OS and maybe lost data as well.

If Win7 Disk Management doesn't do what you want (and it IS extremely limited in what it will do), then download and install either EASEUS Partition Master or Partition Wizard (both of which are FREE) into Win7 and use one of those.

---

### Post by Com:puter$&amp;El3ctron1cs on 2011-08-04
This may be a stupid coment, but I just installed ubuntu 11.04  64 bit. I did have a dual boot with windows 7 before. I decided to get rid of it. I first deframgmented the whole hard drive(windows & ubuntu). Then i backed up my data. I then did a fresh install of ubuntu. The grub config was a little messed up but nothing major. Hope this helps :)

---

