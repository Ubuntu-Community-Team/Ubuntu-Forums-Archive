---
title: "Choice of file system for dual boot with Win7."
date: 2010-07-04
forum: General Help
---

### Post by Aybara on 2010-07-04
I'm gonna setup a dual boot with Windows 7 on my system. My partition layout will be something like this:

Win7 -> ntfs
Ubuntu (root + home) -> ext4
Swap
Data (media & documents) -> ?

What file system should I choose for the data partition? If I go with ext3/4 it seems I can access them from Win7 using a file system driver, but it seems far from safe, from what google tells me. The driver installers aren't for Win7, and I need Ext4 without extents or an ext3-fs with an inode size of 128 to make it work at all.

It saddens me to ask, but should I just go with NTFS?

---

### Post by philinux on 2010-07-04
> **Aybara said:**
> I'm gonna setup a dual boot with Windows 7 on my system. My partition layout will be something like this:

Win7 -> ntfs
Ubuntu (root + home) -> ext4
Swap
Data (media & documents) -> ?

What file system should I choose for the data partition? If I go with ext3/4 it seems I can access them from Win7 using a file system driver, but it seems far from safe, from what google tells me. The driver installers aren't for Win7, and I need Ext4 without extents or an ext3-fs with an inode size of 128 to make it work at all.

It saddens me to ask, but should I just go with NTFS?

Ext4 is a nono for sure.

---

### Post by Aybara on 2010-07-04
Yeah. I did a feeble attempt at ext3, when I launched ext2fsd it first asked if I wanted to "enable forced ext3 write support", and then it didn't recognize the partitions at all. 

Ubuntu/Linux has full and safe support for ntfs, right? If so, maybe it's not the worst thing to use, since this will only be a media partition?

---

### Post by philinux on 2010-07-04
ext2/3 or ntfs I guess.

---

### Post by ajgreeny on 2010-07-04
I think ntfs is the only sensible option, frankly, for the data partition.  That way windows7 will "mount" the partition automatically without you needing to run a separate driver for ext2 or ext3.

Ext4 is out of the question completely as far as I can make out, as the windows fs drivers do not yet work for ext4.

---

### Post by atomizer on 2010-07-04
I would go for: 

Win7 -> ntfs
Ubuntu (root) -> ext4
Swap
Ubuntu (home) -> ext4
Data (media & documents) -> ntfs

I recommend a seperate home and formatting the Data partition in Win7

---

### Post by Leppie on 2010-07-04
there's some support for reiserfs and hfs+ in windows as well.
however, ntfs is probably the best choice.

---

### Post by Aybara on 2010-07-05
Thank for the advice. Ntfs it is :)

---

