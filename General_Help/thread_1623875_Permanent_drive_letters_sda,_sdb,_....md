---
title: "Permanent drive letters sda, sdb, ..."
date: 2010-11-17
forum: General Help
---

### Post by PaNtHeR on 2010-11-17
Hi, 

we are in process of switching from WAMP to LAMP and we picked Ubuntu as our OS of choice. However we have some issues with constant drive letters changing at reboot.

System has 3 HD drives (2 SATA + 1 USB). I edited /etc/fstab to suit my needs and everything works OK until next reboot. 

Sometines USB drive is mounted as sda, sometimes as sdb etc.

Please help because this just can't be right :)

---

### Post by sisco311 on 2010-11-17
Instead of device names use UUIDs: [uhelp]community/UsingUUID[/uhelp].

---

### Post by nothingspecial on 2010-11-17
Use uuids instead, they don`t change

eg ```
UUID=b3d74959-a2ed-447b-8b58-4bf9ac9b7eee /home           ext3    defaults        0       2
```

or labels

eg ```
LABEL=backup /media/backup ext3 defaults 0 0 
```

---

### Post by CharlesA on 2010-11-17
Mounting by UUID would be the best way to go about it. Labels also work, but I've found it easier for me to just use the UUID (even tho there isn't any difference in the fstab config between the two)

---

### Post by PaNtHeR on 2010-11-17
Wow, thank you all for swift response. I'll try this later.

This forum is awesome. 

Cheers.

---

