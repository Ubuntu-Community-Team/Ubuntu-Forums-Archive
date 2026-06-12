---
title: "usb drive two partitions (fat32), windows ingores 2nd"
date: 2010-01-31
forum: General Help
---

### Post by manolo_asdf on 2010-01-31
with gparted i formatted my usb drive with two partitions (1st live ubuntu, 2nd data). both are formatted with type fat32.

unfortunately windows xp does not recognize the 2nd partition. i know this is no win xp support forum, but maybe something went wrong on the gparted side?

has somebody had same problem, partitionin gusb on linux with gparted but didn't have access to all partitions on windows xp?

thanks.

---

### Post by chewearn on 2010-01-31
WinXP can't recognised more than one partition on a flash drive.  It's just a missing feature, that's all.

---

### Post by manolo_asdf on 2010-01-31
damn!

maybe it makes sense to change partitions. to make the data partition the first one and the booting partition (live ubuntu) the second one with bootable flag.

for the evil sometimes i have to transfer data from win-xp boxes and therefore need the data partition accessible.

---

### Post by insane_alien on 2010-01-31
> **chewearn said:**
> WinXP can't recognised more than one partition on a flash drive.  It's just a missing feature, that's all.

seriously? i thought this would have been basic functionality at least included in a service pack.

---

### Post by chewearn on 2010-01-31
> **insane_alien said:**
> seriously? i thought this would have been basic functionality at least included in a service pack.

There is a workaround, to flip the "removable media bit" in the flash drive.  Then, it will be treated as external hard drive and the partitions will show up.

[http://www.google.com/search?name=f&hl=en&q=winxp+more+than+one+partition+on+flash+drive](http://www.google.com/search?name=f&hl=en&q=winxp+more+than+one+partition+on+flash+drive)

---

