---
title: "Problem when partitioning"
date: 2009-08-19
forum: General Help
---

### Post by j_arquimbau on 2009-08-19
Hello!
At the beginning I had 1 primary partition formatted as ntfs (sda1) and an expended partition with (in this order) an OsX partition (htf?), another ntfs one, a swap partition and an ext4 partition.

I didn't need the Mac partition any more so I decided to delete it, move the second ntfs partition, move the swap and expand the ext4 one.

The problem is that everything went OK until I got to the last point. Gparted told me something had failed.

When I restarted the grub failed but I aimed to fix it with a live CD.

The problem is that the ext4 partition (now 40Gb) seems to be used in 25 Gb, but that is imposible because the previous partition was only 20Gb and I still had free disk space. I think this is due to the fact that it wasn't properly repartitioned.

Although it works fine, I would like to have more free space.

Does anybody now how I can free disk space?

---

### Post by Lars Emil Gutt on 2009-08-19
You can boot from a live cd, and then choose to try and not install. Then open Gparted and move around with the partitions :)
Something might go wrong though, and you might have to reinstall if it does go wrong...

---

### Post by j_arquimbau on 2009-08-19
That's in fact what I did and it all went OK except for the last point which consisted on moving and resizing the partition, and Gparted announced  a mistake. The thing is that it's been moved and resized but the data contained in the partition has misteriously grown up like 10 Gb.

---

### Post by Lars Emil Gutt on 2009-08-19
Strange.. Something like that happend to me a couple of weeks ago. I had to reinstall.

---

