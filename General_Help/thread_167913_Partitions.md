---
title: "Partitions"
date: 2006-04-29
forum: General Help
---

### Post by danielduarte on 2006-04-29
I have Windows XP and Ubuntu installed. My Windows' partition size is 60, while ubuntus is 5gb. I was trying to resize the ubuntu's partition (with Partition Magic 8) to 15gb, but, when it's applying the changes, and error occurs. Something like "ext2 error", i dont remember. What am i supposed to do?

---

### Post by ZylGadis on 2006-04-29
To start with, don't use windows software for linux things. GParted is your friend, and I hope you have not ruined your ubuntu partition already.

---

### Post by bluevoodoo1 on 2006-04-29
[QUOTE=ZylGadis]To start with, don't use windows software for linux things. GParted is your friend, and I hope you have not ruined your ubuntu partition already.[/QUOTE]


That is very true and the gparted LiveCD is great.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I don't think partition magic can handle ext2/ext3 file systems... I hope you can still bootup into Linux.

---

### Post by Irony on 2006-04-29
See this [http://ubuntuforums.org/showthread.php?t=142503](http://ubuntuforums.org/showthread.php?t=142503) for how to shrink your Windows ntfs partition - I shrunk mine from 60G to 10G.

With the free space you create you can then copy Ubuntu from where it is into a new partition; [http://ubuntuforums.org/showthread.php?t=129300](http://ubuntuforums.org/showthread.php?t=129300)

---

