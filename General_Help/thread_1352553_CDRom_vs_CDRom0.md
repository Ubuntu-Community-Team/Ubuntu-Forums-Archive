---
title: "CDRom vs CDRom0"
date: 2009-12-11
forum: General Help
---

### Post by Rytron on 2009-12-11
Hi.

Can someone explain why there is a CDRom and a CDRom0 entry under /media?

As I have only one CD drive, shouldn't there be only on CD Rom directory?

Also, the CDRom folder has a link symbol on it.

---

### Post by amauk on 2009-12-11
/media/cdrom0 is the actual mount point of your cd drive

/media/cdrom is just a link to your "primary" cd mount point (in case you have multiple drives, or mount an ISO image as a cd drive)

It's safest to use /media/cdrom
as this will always point to your primary optical drive

---

### Post by Rytron on 2009-12-12
Thank you amauk. Very well explained. :D

---

