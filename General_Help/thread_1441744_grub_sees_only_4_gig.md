---
title: "grub sees only 4 gig"
date: 2010-03-29
forum: General Help
---

### Post by ub007 on 2010-03-29
I got a 450 GB hard drive from which ubuntu boots from.
However when i look at grub,
grub> geometry(hd0,0)
and do the cylinder/head/sector math, it only comes to 4GB instead of 450gig.
Any idea why it sees only 4G?

Cheers
David

---

### Post by zvacet on 2010-03-29
Did you installed Ubuntu on 4GB partition and rest is unallocated space or you used entire disc to install Ubuntu?

---

### Post by oldfred on 2010-03-29
Is it a NTFS partition. This says there was a bug in grub.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

There is a bug in Grub 2, which prevents Grub2 to read any files on an  ntfs partition  beyond the first 4GB.  If any of the boot files is  outside of the 4GB limit, booting  will fail.

---

### Post by ub007 on 2010-04-06
nope, not ntfs.....however ubuntu is installed on seperate hard drive. I got six other disks (1 TB each ) in a RAID 5 configuration and got ext3 on it.
so effectively ubuntu boots from this 1 disk and the remaining 6 drives in a RAID5 config acts as storage.

---

### Post by john newbuntu on 2010-04-06
Try:
geometry(hd0)

---

