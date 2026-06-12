---
title: "ntfs hdd, possible to mount on boot?"
date: 2009-07-27
forum: General Help
---

### Post by Cobbs on 2009-07-27
It's a little inconvenience, but I haven't been able to find a fix for it.  I have a 80gb SATA HDD that I have all my music stored on, however the drive is in a ntfs format since it was created on my windows box originally. I can click on it and it mounts, but I was wondering if there is a way to set it to mount on boot so that I don't have to update amarok/rhythmbox everytime I want the music to show?   

Tried looking around for a post on this, most of which suggested formating the drive because of ntfs drives not recognizing the unix boot commands. I would rather not lose the music stored there, so if there if someone could point me in the right direction at correcting the mount issues I would be most appreciative.

Thanks!

---

### Post by statistic on 2009-07-27
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

That should help you, you can skip the ntfs-3g installation instructions though, ubuntu comes with it nowadays.

---

### Post by binbash on 2009-07-27
you will only do fstab part.

---

