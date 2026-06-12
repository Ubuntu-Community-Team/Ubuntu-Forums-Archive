---
title: "I/O errors but smart data says hhd is OK?"
date: 2011-11-08
forum: General Help
---

### Post by jonnyboysmithy on 2011-11-08
I'm getting I/O errors and cannot read disk errors.
Sometimes the system locks up and I push ctrl+alt+F1 and I'm told I've got a bad superblock. I thought my hard drive might be dying but disk utility reports the drive as healthy.
I've also had a kernel panic and swap read problems.
I'm running Ubuntu 11.04

So my question is: is my disk dying? and why am I getting all these errors?

---

### Post by mcduck on 2011-11-08
Perhaps the errors happen because of something else than the disk itself? Any problems with power, SATA controller, the filesystem,  or of course simply the cable in use could result in I/O errors.

Anyway, I'd recommend checking the SMART data using some other tool, just to be sure. Usually the best approach is to use the SMART check tool from the hard drive's manufacturer's web site.

---

### Post by dcstar on 2011-11-08
> **mcduck said:**
> Perhaps the errors happen because of something else than the disk itself? Any problems with power, SATA controller, the filesystem,  or of course simply the cable in use could result in I/O errors.
.........

And if your CPU or other chips on the MB overheat, then things like this can occur.

---

### Post by jonnyboysmithy on 2011-11-09
> **dcstar said:**
> And if your CPU or other chips on the MB overheat, then things like this can occur.
I think this maybe the case, the cpu runs cool but the ram is usually pretty hot.
I hadn't really considered that.

EDIT: after doing some reading, I'm sure its the ram thats just cooking. Sometimes Ive had the cpu run @ 65ish celsius, on a bed with no ventilation and the ram just doesn't get any air circulation. Typically the crashes happen when I'm working on my bed.

---

### Post by jonnyboysmithy on 2011-11-09
> **mcduck said:**
> Perhaps the errors happen because of something else than the disk itself? Any problems with power, SATA controller, the filesystem,  or of course simply the cable in use could result in I/O errors.

Anyway, I'd recommend checking the SMART data using some other tool, just to be sure. Usually the best approach is to use the SMART check tool from the hard drive's manufacturer's web site.
I'm running a Dell latitude laptop (d610) no trouble whatsoever with the controllers, I don't think power is an issue. Its probably the heat...

---

