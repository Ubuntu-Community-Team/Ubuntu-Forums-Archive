---
title: "Unable to mount"
date: 2011-01-06
forum: General Help
---

### Post by avinashphoneix on 2011-01-06
hi friends pls help me to my problem i don't know how to do, my problem was
when i put my pendrive and also external harddrive it should tell some error message. The message was (Unable to mount
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media)so pls help me.........

---

### Post by TeoBigusGeekus on 2011-01-06
```
sudo chown yourusername /dev/sdb1
```
from terminal and try again

---

