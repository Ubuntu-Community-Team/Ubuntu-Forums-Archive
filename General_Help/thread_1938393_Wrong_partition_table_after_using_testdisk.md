---
title: "Wrong partition table after using testdisk"
date: 2012-03-09
forum: General Help
---

### Post by El Caballero on 2012-03-09
Hello.
A friend of mine erased the Photos directory by mistake. To recover it he booted from a livecd and ran Testdisk. Everything went fine (apparently), but when he restarted the computer, the disk could not be mounted. Further investigation showed us that the partition table seems to have been rewritten to:

[IMG]http://img52.imageshack.us/img52/4780/diskscreenshot.png[/IMG]

Before it had a single 296GB at the beginning of the disk (/dev/sda1) followed by the extended and swap partitions. Is there any way to recover/restore the partition table?
Thanks in advance.

---

