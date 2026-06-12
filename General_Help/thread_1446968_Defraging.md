---
title: "Defraging"
date: 2010-04-04
forum: General Help
---

### Post by DaveMcC on 2010-04-04
Being new to the world of Ubuntu ? Linux etc, I have been downloading deleting all types of fills just to get the feel of the system.

Now! if the same was done in windows after a wile it would need defraged, do you have to do the same with Ubuntu?

:lolflag:

---

### Post by coffeecat on 2010-04-04
No. :wink:
















The ext3 or ext4 filesystem you are using will not get significantly fragmented until it's more than about 90% full. If anyone tells you that Linux filesystems do not get fragmented, do not believe them. Most (all?) filesystems can get fragmented, but it's not a significant problem in Linux.

---

### Post by conradin on 2010-04-04
Disk checks are routine scheduled processes in Linux for every 30 mounts or 180 days whichever happens first. 

Disk checks in MS windows are user initiated and often neglected for years.

---

