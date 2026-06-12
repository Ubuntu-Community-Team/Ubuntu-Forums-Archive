---
title: "Resizing an extended partion"
date: 2010-03-06
forum: General Help
---

### Post by mortalapeman on 2010-03-06
When I first got my computer, I though I'd be needing more space than I thought for my windows 7 partition for games and such. Now I want to delete the recovery partition, resize the windows one and add it all to the extended partition that contains all the stuff for Ubuntu. When I try to use gparted, I can do everything except resize or move the extended partition. I assume becasue there is the graphic of a lock next to it, that means I can't edit my Ubuntu partition the normal way.

Is there anyway to resize and move my extended partition? Google hasn't been much help on this one.

Thanks guys

---

### Post by spiderbatdad on 2010-03-06
are you using gparted live? You can't resize the partition while its mounted.

---

### Post by dcstar on 2010-03-06
> **mortalapeman said:**
> When I first got my computer, I though I'd be needing more space than I thought for my windows 7 partition for games and such. Now I want to delete the recovery partition, resize the windows one and add it all to the extended partition that contains all the stuff for Ubuntu. When I try to use gparted, I can do everything except resize or move the extended partition. I assume becasue there is the graphic of a lock next to it, that means I can't edit my Ubuntu partition the normal way.

Is there anyway to resize and move my extended partition? Google hasn't been much help on this one.

Thanks guys

Boot off the Ubuntu Install CD to do this.

---

### Post by mortalapeman on 2010-03-06
> **spiderbatdad said:**
> are you using gparted live? You can't resize the partition while its mounted.


I was using gparted from puppy linux booted off a USB. Will it work better if I use it off the Ubuntu live CD? I thought it wouldn't matter.

---

### Post by spiderbatdad on 2010-03-06
yes dcstar's suggestion is more likely to work if you have formatted to ext4...it may be that puppy doesn't recognize the file system.

---

