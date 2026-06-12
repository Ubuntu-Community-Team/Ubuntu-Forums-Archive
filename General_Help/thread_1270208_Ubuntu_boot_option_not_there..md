---
title: "Ubuntu boot option not there."
date: 2009-09-19
forum: General Help
---

### Post by johan34 on 2009-09-19
I had my hard drive with 2 partitions. 1 with ubuntu, 1 with XP. After a problem with XP, i decided to reinstall XP. when xp installation asked me to choose a partition, I chose the 1 with the old XP on it and deleted it. I then formatted that unused space and XP installed. The ubuntu partition is still there (I confirmed with a live cd.) but It does not show the ubuntu option in the boot menu. What do i do?

---

### Post by marcopolo1981 on 2009-09-19
You will need to reinstall the GRUB boot loader.
Easiest way is to download the super grub disc from [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and follow instructions at the same site, but found in the forums section

Mark

Edit
Once you have downloaded SGD, please follow the instructions at [http://www.supergrubdisk.org/w/index.php5?title=Howto_Fix_Grub](http://www.supergrubdisk.org/w/index.php5?title=Howto_Fix_Grub)

---

### Post by johan34 on 2009-09-19
How do i download it? and do i do it with a live cd or XP?

---

### Post by marcopolo1981 on 2009-09-19
OK, sorry. I was rushing ahead without reading your full post.

From within XP, go to [http://www.supergrubdisk.org/index.php?pid=12](http://www.supergrubdisk.org/index.php?pid=12) and click the green download button.

Once the EXECUTABLE FILE has been saved, go to [http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk) and follow their instructions.

This way saves you from going the live cd method.

Mark

---

### Post by johan34 on 2009-09-19
Yes! it worked. Thnku. My parents got freaked n thought i messed it badly!

---

### Post by marcopolo1981 on 2009-09-19
No worries. Glad I could help!

Mark

---

