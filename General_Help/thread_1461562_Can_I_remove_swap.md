---
title: "Can I remove swap?"
date: 2010-04-24
forum: General Help
---

### Post by Steven_S on 2010-04-24
I have installed UNR on my little Asus eeepc701, and all works well. However, I would like to make sure the SSD is spared a bit by removing swap completely (the SSD is too small anyway to hibernate). 

Is it possible to do that even after I have installed it? I have tweaked it quite a bit already, and don't want to loose what I have removed and installed already... 

Oh, and of course: if it is possible - how to do it? :-)

---

### Post by Ayuthia on 2010-04-24
I could be wrong, but I think that the swap is defined in /etc/fstab.  You can comment it out in there.

---

### Post by 2hot6ft2 on 2010-04-24
You would have to boot the livecd and open
System > Administration > GParted
Right click on the swap partition and select swapoff
And right click on anything else with locks on it and select unmount.
Then you can delete the swap partition if you want and make the changes to expand another partition to take up that space.
Click Apply to make the changes.

---

### Post by Steven_S on 2010-04-24
I'll give that a try - many thanks!

---

### Post by 2hot6ft2 on 2010-04-24
> **Steven_S said:**
> I'll give that a try - many thanks!
You're welcome. Just make sure you don't delete something you want to keep.

---

### Post by Steven_S on 2010-04-24
I just came back for a little update: the solution presented works perfect. Thanks again!

---

