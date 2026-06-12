---
title: "mount FreeNAS ufs partition"
date: 2010-11-25
forum: General Help
---

### Post by jomex on 2010-11-25
How can I mount a FreeNAS UFS partition in Ubuntu?

I already tried: [http://blog.hani-ibrahim.de/en/freenas-ufs-datentraeger-mounten.html](http://blog.hani-ibrahim.de/en/freenas-ufs-datentraeger-mounten.html)
and several other sources which basically say the same thing...

 modprobe ufs
 mount -t ufs -ro ufstype=ufs2 /dev/sda1 /mnt/freenas
 dmesg|tail

I always get "bad magic number" :/

---

