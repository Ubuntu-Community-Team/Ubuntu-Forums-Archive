---
title: "Mounting a drive in Kubuntu"
date: 2009-07-06
forum: General Help
---

### Post by JauntyJackalope88 on 2009-07-06
I am a Linux newbie, so I appologize if I ask a obvious question. 

How do you mount a drive in terminal? I know part of the command:

mount -t 

But I'm having trouble. Can someone tell me the whole command 
and explain it.

Many thanks!
JJ88

---

### Post by HavocXphere on 2009-07-06
```
sudo mount -t ntfs-3g /dev/disk/by-uuid/EE3091BD30918D69 /media/FreeAgent
```

-t  = Used detailed mount command specifying type location etc.

ntfs-3g = Type of filesystem being mounted. The 3g part refers to the driver being used.

/dev/disk/by-uuid/EE3091BD30918D69 = code identifying the partition to be mounted. Use either blkid or ls -l /dev/disk/by-uuid to find the code.

/media/FreeAgent = location to mount it to. Make sure the folder exists and that you have write access.

---

### Post by JauntyJackalope88 on 2009-07-06
Thanks!

---

### Post by oldos2er on 2009-07-06
```
man mount
```

---

