---
title: "Mount point for external hard disk"
date: 2010-01-11
forum: General Help
---

### Post by Nonno Bassotto on 2010-01-11
I have just updated to karmic, and I found that my external hard disk partitions, previously mounted under /media/disk and /media/fat are now referenced by something looking like a UUID, namely /media/7b096ea4-60ee-46b1-95cd-1851b051c40d and /media/4951-95D9.

Is there a way to revert to the old settings? Any application relying on the files on the external hard disk has now stopped working. While I certainly could just change reference (assuming the UUID does not change every session), I'd rather use the old names if possible.

---

### Post by Leppie on 2010-01-11
unmount the drives and change the labels (to the old mount points).
you can use gparted or something similar for that, if there's ntfs partitions/disks you may have to install ntfsprogs as well:
```
sudo apt-get install ntfsprogs
```

ps: are you a short grandpa???

---

### Post by warfacegod on 2010-01-11
System> Admin.> Disk Utilities should work.


ps: are you a short grandpa???

Leppie, stop being mean to the elderly. Ha. Ha.

---

### Post by Nonno Bassotto on 2010-01-11
Thank you very much, it worked. :D

---

### Post by Nonno Bassotto on 2010-01-11
> **Leppie said:**
> are you a short grandpa???

Sort of :)
In Italy Nonno Bassotto is the name of a Disney character, being the grandpa of the Beagle Boys

---

### Post by Leppie on 2010-01-12
glad it's all sorted.

non sono molto familiare con i personaggi disney in italiano.

---

