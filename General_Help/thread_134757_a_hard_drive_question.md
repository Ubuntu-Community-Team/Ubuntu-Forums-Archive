---
title: "a hard drive question"
date: 2006-02-22
forum: General Help
---

### Post by jpbleuu on 2006-02-22
i have added a second hard drive to this system. i was able to partition it, and i formatted it in the ext3 file system. i have also mounted it in /mnt/hdb1 and created a entry in fstab so that it will mount automatically.

my question is this, now that the hard drive is partitioned and formatted and what not, should i be able to go into places, then computer to see whats on the hard drive? if so how does one go about this? and if not then am i just suppose to go into the hard drive by goign to mnt/hdb1?

Thanks.

---

### Post by Ramses de Norre on 2006-02-22
Yes you are, that's what the mount point is about. The idea is to have all your files under / in one big tree, so a new partition is added somewhere under / (can be anywhere I think).
There is no such thing as a drive letter as in windows. But you can add the mount point to the places menu if you want to.

---

### Post by jpbleuu on 2006-02-22
thanks, that is what i thought. but i just wanted to make sure.

---

### Post by nrwilk on 2006-02-22
It can be anywhere, but ubuntu will only show devices whose mount point is under /media/ on the desktop.  So, if you want there to be an icon on the desktop for the mounted drive, mount it under /media/hdb2 (or any name you want).  You can still make a link to the drive on the desktop manually, but this way ubuntu will do it for you.

---

