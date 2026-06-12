---
title: "Cannot change owner of partition"
date: 2011-04-09
forum: General Help
---

### Post by l07 on 2011-04-09
I cannot write files to an ext4 partition I created unless using gksu nautilus, so I tried ```
sudo chown my_user /dev/sda3
``` but the owner is still reported in the properties to be root. /dev/sda3 is the path I see in gparted.

---

### Post by l07 on 2011-04-09
I just used gksu nautilus to change permissions so it works now, but why didn't
sudo chown my_user /dev/sda3?

Also why are root permissions in folder access listed as "access files" only if it can create and delete files?

---

### Post by oldos2er on 2011-04-09
I think you would need to use **sudo chown -R user:user /media/storage** for example[B].
[/B]

---

### Post by WorMzy on 2011-04-09
You don't chown the block device, you chown the root directory of the file system.

e.g. if the filesystem is mounted to /media/storage, you would run
```
sudo chown -R username:group /media/storage
```

---

### Post by garvinrick4 on 2011-04-09
[QUOTE=l07;10658204] answered

---

### Post by oldos2er on 2011-04-10
> **WorMzy said:**
> You don't chown the block device, you chown the root directory of the file system.


Thank you. I'll edit my post appropriately.

---

### Post by l07 on 2011-04-11
Thanks.

---

