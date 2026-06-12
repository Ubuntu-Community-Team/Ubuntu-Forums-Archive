---
title: "Mount two devices, concatenated"
date: 2010-04-13
forum: General Help
---

### Post by leodp on 2010-04-13
Hi all,
I need to  store a big file in my tablet (Nokia N800 running Linux for ARM).
The file is about 8.5GB and cannot be splitted. 
I have a 8GB SSD card plus a 4GB SSD card in the tablet.

Does anybody know if it is possible to mount the two devices concatenated at a single mount point, in order to have 12GB space?

Thanks,Leo

---

### Post by WinterRain on 2010-04-13
Try compressing the file so it will fit on the 8gb card.

---

### Post by FiReiSFuN on 2010-04-13
Short answer: no.
Complicated answer: use LVM - if you are using LVM already (I don't know anything about the ARM version so I don't know if this is even possible), then you can make both drives part of the same volume group and mount the combined space at one mountpoint.

---

### Post by leodp on 2010-04-13
Hi all,
cannot compress, it's a big file I'm downloading with torrent.
I do not have LVM. I think it's possible, probably I need to recompile the kernel.

Thanks for the hints,
Leo

---

