---
title: "Need help mounting (or extracting data from) possibly corrupted filesystem"
date: 2011-07-10
forum: General Help
---

### Post by reuben on 2011-07-10
A friend of mine corrupted his camera card while on vacation; he was unable to recover many photos from it via his windows system (he tried a bunch of photo recovery apps, and got maybe 30% of his photos back.) I told him to take an image of the filesystem, and upload it to a server of mine, so I could take a look.

A couple questions. 

First of all, how do I mount usbfs or umsdos partitions? Either way, I get an error from mount: **mount: unknown filesystem type 'usbfs'** / **mount: unknown filesystem type 'umsdos'**; this despite mount's man page advertising the ability to mount these types.

Second, if I'm unable to mount once I have also tried the above types (I've already tried msdos and ntfs, unsuccessfully), any suggestions on a way that I scan through a filesystem image looking for files, e.g. by fileheader? My guess is that the filesystem metadata got corrupted on the card, so the image that he made probably won't be mountable.

---

### Post by reuben on 2011-07-10
Hm, update. Found "foremost", which I'm trying. Will edit this on success. Still could use some advice on the mount question.

---

