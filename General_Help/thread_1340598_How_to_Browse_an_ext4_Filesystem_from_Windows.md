---
title: "How to Browse an ext4 Filesystem from Windows"
date: 2009-11-28
forum: General Help
---

### Post by mikeac72 on 2009-11-28
[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

You need to have booted from the LiveCD, and used that "Try Ubuntu" feature.  Use GParted to create the ext4 filesystem using step 1 in the link, and install ubuntu in that partition.  It disables the extent feature, which can somewhat slow down your OS.
Instead, block mapping is used, as it was used in the ext2 and ext3 filesystems.

Ext2fsd works with any Windows OS above XP/2003.

---

### Post by mikeac72 on 2009-11-29
Wow.  I expected lots of replies.

---

### Post by Clancy_s on 2009-11-29
Looks interesting, I've been putting off KK install 'til I have time to repartition my system and do a clean install: I'll try it then.

I'm wondering what the 'extent' feature is and what difference disabling it makes...

eta: after reading 2 things occur to me -

the link says > When creating the ext4 filesystem, make sure to add &#8220;-O ^extent&#8221; which means disabling the &#8220;extent&#8221; feature bit.

All the articles I've seen say that extents are enabled / disabled when mounting the file system, not when creating it.

Extents are used to speed up file writing, so by disabling them you'll loose at least some of the speed advantages of ext4.  I'll probably have a shared partition as ext4 -o noextents and leave the other extents enabled for ubuntu data, / and /home.

Or stick with ext 3 or fat32 for shared data...

---

