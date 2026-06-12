---
title: "cant boot xp"
date: 2009-09-08
forum: General Help
---

### Post by sp0onman on 2009-09-08
hey all, im back using ubuntu after a year or so off it. So my problem is that i used gparted to shrink my ntfs partition to create space for my ubuntu partition. ubuntu has installed fine, but now i cant boot into xp. after selecting it on the grub menu it just hangs at "windows is starting..." or something like that.

I'm a total noob to this kind of stuff could someone give me a hand in finding the problem, and hopefully fixing it. i dont know what info i should be giving you though.
thanks

---

### Post by oboedad55 on 2009-09-08
> **sp0onman said:**
> hey all, im back using ubuntu after a year or so off it. So my problem is that i used gparted to shrink my ntfs partition to create space for my ubuntu partition. ubuntu has installed fine, but now i cant boot into xp. after selecting it on the grub menu it just hangs at "windows is starting..." or something like that.

I'm a total noob to this kind of stuff could someone give me a hand in finding the problem, and hopefully fixing it. i dont know what info i should be giving you though.
thanks

Did you defrag your drive before partitioning? I hosed a Windows partition once because I didn't defrag prior to resizing. Hopefully you backed up any data you may need. I hope I'm wrong, but it sounds like you bricked Windows.

---

### Post by sp0onman on 2009-09-08
nah i didn't defrag. i read that problems like this can be repaired with testdisk?

---

### Post by sp0onman on 2009-09-08
i tried running the repair console with the xp disk, and using the fixmbr command then i reinstalled the grub menu with the ubuntu live cd. it didnt work.

---

### Post by P4man on 2009-09-08
can windows boot in recovery mode (F8 during boot I think) ?
If not, did you just resize, or also move the windows partition? Windows can only boot the first partition on the hdd. If you moved it elsewhere, it won't work.

---

