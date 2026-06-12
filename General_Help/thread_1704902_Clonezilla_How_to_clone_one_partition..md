---
title: "Clonezilla: How to clone one partition."
date: 2011-03-11
forum: General Help
---

### Post by mn_voyageur on 2011-03-11
Using Clonezilla, is it posible to image just the primary and not the secondary partition of an hdd?  

sda1 has my system and software files.  sda2 does not require imaging.

When I ran clonezilla, it imaged the entire drive.  (both partitions)  I then sucessfully installed the image on a second drive.  However, I really only want to image the first partition.

Thanks,
MarkN

---

### Post by cbowman57 on 2011-03-11
Yes, it will image separate partitions.  When it boots up you should have the option to do partitions instead of drives but drives is the default.  If your version won't then you might have to get a more recent one.  I use 1.2.8-3 on my system, which might be the testing version.

---

