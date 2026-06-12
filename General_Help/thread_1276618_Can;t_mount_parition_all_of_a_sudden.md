---
title: "Can;t mount parition all of a sudden?"
date: 2009-09-27
forum: General Help
---

### Post by biinarii on 2009-09-27
OK, so I had this partition mounted wich contains a couple of movies. I left ubuntu running when I went out and when I came back ubuntu was frozen so I rebooted it.

If I select my partition from "places"
 I get the following error:

Unable to mount 107.0 GB Media
The volume uses the  file system which is not supported by your system.


This is a clean ubuntu installation and the partition is fat32..?

Anyone formiliar with this problem??

---

### Post by oldfred on 2009-09-27
I might try fsck first.
sudo /sbin/fsck.vfat -V <the fat32 device>

In my case it was:
sudo /sbin/fsck.vfat -V /dev/sdc3

---

### Post by scouser73 on 2009-09-27
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

