---
title: "Ubuntu partition take over some free space."
date: 2010-03-20
forum: General Help
---

### Post by The Thunder Chimp on 2010-03-20
How do I get to take over some free space on my harddrive with ubuntu. Kparted let's me delete some partitions, but not take some over from existing partitions.

---

### Post by mac666 on 2010-03-20
please post a screenshot of your gparted

---

### Post by drs305 on 2010-03-20
Take a look at this guide to expanding / . Start about half way down the first post at the "some basic rules" section.
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

The main tip to moving around/resizing partitions is that they be unmounted, and some cannot be unless you are running the LiveCD or a "rescue" CD. This includes unmounting the swap partition, even if you are running the LiveCD.

---

### Post by The Thunder Chimp on 2010-03-21
Okay thanks, I'll take a look a that. I'll come back if I need so. I'll mark as Solved as soon as it works.

---

### Post by The Thunder Chimp on 2010-03-21
Here, I have managed to take over with ubuntu some space that was originally in the big Linux partition, but I can't manage to take over some unalocated space (10GB) that's neither with Linux or Windows (Windows is the biggest one (biggest windows needs more than Linux)). According to drs305's link, it can't be done. Does anyone know however, how we can expand the Extended partition?

---

### Post by The Thunder Chimp on 2010-03-21
The above comment's operations were done with a bootable flash drive by the way.

---

### Post by Helkaluin on 2010-03-21
You can expand the extended partition. The link by drs305 only states that resizing can't be done in the case of logical partitions trying to exceed the extended paritions' limits.

One thing to keep in mind is that, since you have the swap inside the extended, and there's a key-icon next to it. I suspect you need to deswap first.

After that all should be fine.

---

### Post by drs305 on 2010-03-21
It can be done. As the previous poster stated, you have to unmount the swap partition first and you also have to expand the extended partition (sda3) before you can expand sda5.

The easiest way of expanding sda3 will be to first highlight it in the bottom pane and then drag it's left light blue border all the way over to touch sda2. Make sure you are dragging the light blue border and not the dark blue border of sda5. Once you have done that you can expand sda5.

---

