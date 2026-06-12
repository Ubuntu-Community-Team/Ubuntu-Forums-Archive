---
title: "ubuntu 10.04 hard disk error"
date: 2010-10-16
forum: General Help
---

### Post by mosaic2s on 2010-10-16
I have got 500gb seagate HDD installed on my system. No division of HDD. Running fully updated 10.04 for last 4 months or so.

Yesterday the system started freezing. Then when I re-booted after a while, it ran disk check. Froze at 70%. Disk has errors.
Gave 4 options F for fixing, M for manual mount etc, I for ignore. None of the options gave access to GUI. But C for cancel gave a maintenance shell.

How can I get the HDD to recover from bad sector presumably? And get GUI working.
I have taken data backup on another system. Tried installing the HDD there, it gave same error at 70%. Have changed power and data cables to be sure about that.

---

### Post by TeoBigusGeekus on 2010-10-16
Boot up with a live cd, open terminal and
```
fsck /dev/sda1
```
Replace sda1 with your hd.

---

### Post by mosaic2s on 2010-10-16
Sorry.
I had to move ahead.
Have formatted the hard disk into 2 partitions and doing re-install.

Will mark this for next time.

---

