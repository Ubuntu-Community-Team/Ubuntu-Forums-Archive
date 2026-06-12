---
title: "xp/linux dual boot..."
date: 2009-08-29
forum: General Help
---

### Post by tempus on 2009-08-29
i had xp and linux setup as a dual boot but now wish to remove xp from the computer. i want ot get rid  of xp and use the entire hard drive for linux. how is it possible to expand the installation of ubuntu to use the space where xp used to be? is it even possible?

---

### Post by x33a on 2009-08-29
use gparted to delete the xp partition. then, format that space to ext3 or your fav. filesystem. add the respective entry in fstab and you are done.

---

### Post by Woody1987 on 2009-08-29
Boot up a livecd of ubuntu, use gparted to delete xp and you should then be able to expand the existing installation of ubuntu.

---

### Post by tempus on 2009-08-29
the problem is that xp was setup on the primary partition. I deleted xp with no problem in gparted but when i go to the live cd it can format it in ext 3 but it will be still a primary partition. I still cannot expand linux to the primary partition.

---

### Post by louieb on 2009-08-29
> I still cannot expand linux to the primary partition.     Just a thought: 
Unless you really need more space in the Linux partition  (10GB is plenty) Just go ahead and create, format a new partition.  Use it for your music, photos, whatever.  Its really a good idea to keep your data on a separate partition from the OS. Its out of the way if you have to reinstall and it makes creating a backup of just your data a lot simpler.

---

