---
title: "Help - partitions have been renumbered"
date: 2010-11-16
forum: General Help
---

### Post by texla on 2010-11-16
My system recently had all of its partitions renumbered.  Basically, my old partitions were not in numerical order and when I tried to boot in an old windows restore partition (by mistake!)  it renumbered everything in order. 
Is there some way I can put them back in the order I had them in?

---

### Post by texla on 2010-11-18
All fixed now - Problem was with clonezilla partitions not restoring to new SDA numbers.  Decided to stay with the new number order and rename everything in the clonezilla backup partition to match.  Did the trick but I needed to reinstall grub with a Live CD to see it all the way through.  MIght need to disable that Windows rescue partition somehow because that was uncool.

---

