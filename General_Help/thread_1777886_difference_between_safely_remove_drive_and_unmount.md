---
title: "difference between safely remove drive and unmount option"
date: 2011-06-08
forum: General Help
---

### Post by PeterP24 on 2011-06-08
Hello,

Related to an external hdd, I would like to know if there is a difference between the safely remove drive option (from the right click menu) and the unmount option (maybe from the disk utility tool)? The reason is that the safely remove drive option is buggy (a bug which appears to have been propagated from version 10.04 until 11.04) for one of my external drives and I would like to know if I can safely use unmount.

pts

---

### Post by philinux on 2011-06-08
> **PeterP24 said:**
> Hello,

Related to an external hdd, I would like to know if there is a difference between the safely remove drive option (from the right click menu) and the unmount option (maybe from the disk utility tool)? The reason is that the safely remove drive option is buggy (a bug which appears to have been propagated from version 10.04 until 11.04) for one of my external drives and I would like to know if I can safely use unmount.

pts

A search finds this good explanation. Although I disagree with the conclusion. It horses for courses.

[http://ubuntutalk.tumblr.com/post/346018554/the-unmount-eject-and-safely-remove-drive-dilemma](http://ubuntutalk.tumblr.com/post/346018554/the-unmount-eject-and-safely-remove-drive-dilemma)

---

### Post by PeterP24 on 2011-06-08
Ok, after following the link, I still don't know if I understand so I want to check with you: Basically "Safely remove drive means" unmount and power off the attached drive (so being powered off means it cannot be mounted again without reconnecting the external drive) while Unmount means unmount (and leave it powered so that it can be mounted again)?
Given the above mentioned - it is still safe to unplug the device after the unmount command? 

pts

---

### Post by seawolf167 on 2011-06-08
> **PeterP24 said:**
> Given the above mentioned - it is still safe to unplug the device after the unmount command?

Yes, provided there are no other partitions from that device currently mounted.

Basically - unmount unmounts a single partition while safely remove unmounts all partitions of that device.

---

