---
title: "Desperate for help to edit /etc/fstab in recovery mode"
date: 2009-12-28
forum: General Help
---

### Post by Colonel Forbin on 2009-12-28
HELP!

I have edited my fstab file to automount two internal SATA drives. After the edit, the computer won't start up, saying that it could not mount all drives. I have tried editing the fstab file in emacs and vi, but it just says buffer is read only, and will not allow me to delete the offending code. I'm not a complete newbie, not scared of the command line, but I can't figure out what I am doing wrong.

Any help is appreciated!

Colonel Forbin

---

### Post by KiLaHuRtZ on 2009-12-28
You need to remount '/' as read-write.  In single user mode, it mounts as read-only.

```
mount -n -o remount,rw /
```

---

### Post by Colonel Forbin on 2009-12-28
that worked to delete the code, but how do I save the new fstab?

---

### Post by KiLaHuRtZ on 2009-12-28
In vi/vim...

```
[ESC]:wq!
```

---

### Post by Colonel Forbin on 2009-12-29
Thank you Kilahurtz. I was able to recover. Now I've just got to figure out what I did wrong and find the correct way to automount these drives.

---

### Post by QLee on 2009-12-29
> **Colonel Forbin said:**
> Thank you Kilahurtz. I was able to recover. Now I've just got to figure out what I did wrong and find the correct way to automount these drives.

This might help:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Colonel Forbin on 2009-12-29
and thanks to you qlee. That got me going. I had named the drives both by /dev/sda and the uuid. Realized you only need the uuid.

---

