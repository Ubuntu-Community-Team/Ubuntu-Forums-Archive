---
title: "disk recovery tools"
date: 2011-09-11
forum: General Help
---

### Post by noorez on 2011-09-11
Not sure if this belongs in this section:

My macbook pro recently has refused to boot. After trying the disk recovery it told me that there is an invalid node structure. Is there any linux tool that would be able to fix this? Or at least allow me to recover some of my files before i reinstall the os?

---

### Post by TeoBigusGeekus on 2011-09-11
If we're talking about and ext filesystem, boot up with a live cd and give
```
sudo fsck /dev/sda1
```
Replace sda1 with the appropriate partition name.

---

### Post by harlequin_ on 2011-09-11
> **noorez said:**
> Not sure if this belongs in this section:

My macbook pro recently has refused to boot. After trying the disk recovery it told me that there is an invalid node structure. Is there any linux tool that would be able to fix this? Or at least allow me to recover some of my files before i reinstall the os?

Well, I do not know about Apple computers, but for a PC (if Windows is the OS that refuses to boot) you can recover your files with a simple Live CD, using the file browser. Maybe it's possible in Macs too..

---

### Post by noorez on 2011-09-11
The filesystem in question is the HFS+. The default for the newer os x versions.

---

### Post by Sef on 2011-09-11
check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

