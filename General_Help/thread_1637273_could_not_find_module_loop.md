---
title: "could not find module loop"
date: 2010-12-04
forum: General Help
---

### Post by haljk on 2010-12-04
I'd like to mount an iso file ,however, it failed as following:

ljk@ljk-laptop:~/Test$ modinfo loop
ERROR: modinfo: could not find module loop

what I can do?

---

### Post by Lorem on 2010-12-04
I get the same info, but mounting isos works:
```

sudo mkdir /media/myiso
sudo mount -o loop /home/user/myiso.iso /media/myiso

```Adjust the paths as you need.

When you're done, type ```
sudo umount /media/myiso
``` to unmount the iso. If you want, you can delete the folder after unmountung:```
sudo rm -r /media/myiso
```

---

