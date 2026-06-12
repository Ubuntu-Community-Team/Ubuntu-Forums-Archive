---
title: "Ubuntu ZFS Support"
date: 2010-03-03
forum: General Help
---

### Post by Bradj47 on 2010-03-03
Can 9.10 read ZFS? I'm still using 9.04 and it can't read my Solaris hard drive which is formatted with ZFS. I'm wondering that if I upgraded maybe I could read that drive. What would be even better is if I could format the Ubuntu drive with ZFS before installing so when it was installed I could use the ZFS snapshot and pooling features like I can do on Solaris. So, I was just wondering what Ubuntu's position is on ZFS.

---

### Post by gsmanners on 2010-03-03
File systems have to be rock solid proven for a long time before they can be included into any distro, however there is work being done for ZFS. See [http://zfs-fuse.net/](http://zfs-fuse.net/)

---

### Post by flippo on 2010-03-03
The lack of ZFS isn't necessarily due to instability (although I will admit I have no idea how stable the Linux support is as I don't use ZFS).

ZFS support cannot be included in the kernel due to licensing issues (GNU doesn't work with Sun's license).  Your current only option is the FUSE (Filesystem in User SpacE) extension, which links externally and gets around the GNU free software requirement.

---

