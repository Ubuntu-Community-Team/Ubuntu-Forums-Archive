---
title: "mkisofs."
date: 2012-02-26
forum: General Help
---

### Post by carbquick on 2012-02-26
Am using ubu 10, tried genisoimage(successor to mkisofs;same options); tried to make a bootable cd image
emulation mode. Did:
genisoimage -b /root/t.img -o an.iso /root/tuts ; tuts is dir of files t.img is bootable 2.88 image. genisoimage
found /root/tuts ok but said: "uhoh! I cannot find 't.img'. Then I copied both t.img and tuts into /usr/bin
where genisoimage/mkisofs are located; then in commandline cd'ed to /usr/bin and did:
genisoimage -b t.img -o an.iso tuts ; again, found tuts but "ohno......" no img found. What am I doing wrong?
carbquick.

---

### Post by schily on 2012-02-26
You are not informed correctly: genisoimage is definitely not the "successor" of mkisofs. Genisoimage rather is a 
defective and unmaintained variant from a 7 year old version of mkisofs. If you use genisoimage, you miss half 
of the featores found in a recent mkisofs and you suffer from various bugs in genisoimage that create defective 
filesystem images.

If you like to use the recent original version of mkisofs, you could fetch a recent version from:

[ftp://ftp.berlios.de/pub/cdrecord/alpha/](ftp://ftp.berlios.de/pub/cdrecord/alpha/)

or a binary version from the various friendly people who provide binary packages.



And BTW: the original manpage for mkisofs did also evolve and should help you to learn where to put the boot image.

---

### Post by carbquick on 2012-02-26
schily tnx for the reply. The man I had for mkisofs is as up to date as can be:
-b file.img is the path and filename of the bootable image; "the pathname must be specified relative to the source path
supplied to mkisofs"!!!!!!!!!!!!!!!!!!! WHAT is the "source path supplied to mkisofs" and WHO supplied it? This is total gobledy-gook; Believe me, I would have preferred to use the Feinman createcd133 from windows XP, which always
works; unfortunately, it can only use a 1.44 img, and I need to use a 2.88. I dowloaded the recent mkisofs, and am trying to get it installed; I suspect there is a broken dependancy or some damn thing. I once mentioned the feinman utility to someone on this forum, and he replied:"why don't you use mkisofs like the rest of the world?" THIS IS WHY.carbquick.

---

