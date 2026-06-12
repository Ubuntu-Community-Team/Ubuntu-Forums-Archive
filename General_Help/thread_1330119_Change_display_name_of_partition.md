---
title: "Change display name of partition"
date: 2009-11-18
forum: General Help
---

### Post by ludionisio on 2009-11-18
Hello,

I have Ubuntu 9.10, 9.04 and Windows XP installed. During installation of ubuntu 9.10 I chose the names of mount location for the old ubuntu and linux as /media/ubuntu904 and /media/windows respectively.

When I run nautilus as root the displayed names for these partitions are exactly as I wanted: ubuntu904 and windows. But when I'm doing everything else as a normal user the displayed names are 10GB Filesystem and System, even though the mount locations are still /media/windows and /media/ubuntu904.

How can I make it display the names as it happens when I'm root?

Thanks

---

### Post by P4man on 2009-11-18
Set a volume label. In karmic you can do that with Disk utility (aka palimpsest) or using gparted. At least for linux volumes, for ntfs volumes have a look here:
[http://tuxecute.blogspot.com/2008/09/change-your-ntfs-windows-drive-label.html](http://tuxecute.blogspot.com/2008/09/change-your-ntfs-windows-drive-label.html)

---

