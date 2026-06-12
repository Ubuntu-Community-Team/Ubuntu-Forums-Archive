---
title: "Apt-get update looks into my cd that's not there? How do i remove it?"
date: 2010-05-06
forum: General Help
---

### Post by QueenZ on 2010-05-06
So when i do apt-get update it works but at the end it also looks into my CD (i think) and since i don't have my CD in there it displays this error message...

> W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download, they have been ignored, or old ones used instead.
What does it mean and how do i fix this?

Thanks!

---

### Post by kill4killin on 2010-05-06
> **QueenZ said:**
> So when i do apt-get update it works but at the end it also looks into my CD (i think) and since i don't have my CD in there it displays this error message...


What does it mean and how do i fix this?

Thanks!

System > Administration > Software Sources

Uncheck the box on the first tab that says to check the CD-ROM/DVD

---

### Post by QueenZ on 2010-05-06
thanks a million, that worked! :)

---

