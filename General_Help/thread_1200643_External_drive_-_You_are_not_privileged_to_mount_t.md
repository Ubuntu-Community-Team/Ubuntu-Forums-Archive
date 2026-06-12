---
title: "External drive - You are not privileged to mount the volume"
date: 2009-06-30
forum: General Help
---

### Post by themusicalduck on 2009-06-30
I setup my FreeAgent drive so that it would mount on startup by adding this line to fstab

```
/dev/sdc1	/media/sdc1   ntfs-3g    defaults,umask=0 0 0
```

and also creating directory /media/sdc1. This works fine, but if I decide to disconnect and then reconnect my drive, or switch on the computer while the drive is off, I cannot mount the drive unless I do it with sudo. Clicking on it brings the error 'You are not privileged to mount the volume', but using sudo mount /dev/sdc1 works fine.

---

