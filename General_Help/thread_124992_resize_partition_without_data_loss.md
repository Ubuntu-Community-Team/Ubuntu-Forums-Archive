---
title: "resize partition without data loss"
date: 2006-02-02
forum: General Help
---

### Post by digitalkarabao on 2006-02-02
help.

i have a 40-GB hard drive all ubuntu. now, i need to install Windows (against my will). I would like to know how to resize my partitions to accomodate a Windows installation without data loss.

I need a guide. A step-by-step would be great.  :)

Thanks.

---

### Post by krusbjorn on 2006-02-02
You can easily do it from a graphical interface using (for example) Gparted, which is in the repos. But if you only have one HD, you probably need to do it from a live-cd, since the drive cannot be mounted while editing the partition table.

There are several different live CDs out there. Just find one that contains Gparted or QTparted and you are good to go.

Things seldom go wrong, but it's of course recommended to backup all your data before messing with the partitions. I managed to completely destroy the partition table when resizing a partition a couple of years back. Luckily, i backed up first.

---

