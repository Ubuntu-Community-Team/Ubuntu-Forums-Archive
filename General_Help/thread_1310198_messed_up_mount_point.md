---
title: "messed up mount point"
date: 2009-11-01
forum: General Help
---

### Post by Beggar Su on 2009-11-01
In ubuntu 9.04, my sd card was mounted to /media/disk, but when I did a clean install of ubuntu 9.10, my sd card is mounted to /media/1252-9113. 

Why does it mount with the numbers and how do I set it to just mount the storage devices to /media/disk?

Thank you.

---

### Post by dabnpits on 2009-11-03
I am also having this issue after upgrading to 9.10 from 9.04 on my Dell Mini 9. Used to automount to /media/disk, now it mounts to /media/B35B-5451

I tried using Ubuntu's "Disk Utility"tool, which let me set a label as "disk". But after applying the change, it mounts as /media/DISK (which still breaks my links)

---

### Post by nerdy_kid on 2009-11-03
add a line to /etc/fstab?

I noticed that Karmic likes to mount stuff to wierd mount points like the ones u said...if the mount point doesn't change, why not change the links?

---

