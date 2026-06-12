---
title: "resize partitions windows and ubuntu"
date: 2011-08-03
forum: General Help
---

### Post by jeremyksmith on 2011-08-03
I have two partitions for my dual boot of 11.04 and windows 7. I want to create more space on the windows partition to put music on. When i load up g-parted or p-magic to attempt this, the two partitions are in different sections and I cannot figure out how to use space from the linux partition to extend the windows. thanks in advance!

---

### Post by tommpogg on 2011-08-03
I menaged to resize the partition where Ubuntu was installed once with GParted with no problems.
Nevertheless I'm not sure if it is a good idea to resize the partition containing windows. Has anyone already attempted it with success?

@[jeremyksmith]("http://ubuntuforums.org/member.php?u=1385898"): Why don't you create a third NTFS partition for your music? You could find some place by shrinking the partition with Ubuntu

Anyway, if you are planning to work with patitions, back up your data before

---

### Post by Hatsune Miku on 2011-08-03
> **jeremyksmith said:**
> I have two partitions for my dual boot of 11.04 and windows 7. I want to create more space on the windows partition to put music on. When i load up g-parted or p-magic to attempt this, the two partitions are in different sections and I cannot figure out how to use space from the linux partition to extend the windows. thanks in advance!

It is simple; Shrink the Ubuntu partition, then extend the windows partition to the space you just made. It might take a little time to do because your data will need to be moved to new sectors on the hard disk(Any partition editor does this)

~Miku.

---

