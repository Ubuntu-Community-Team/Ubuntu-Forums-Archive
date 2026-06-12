---
title: "Um Needing help sharing folders"
date: 2010-10-22
forum: General Help
---

### Post by Adrienk on 2010-10-22
I have virtual Box 3.2.X (the latest version) and I have windows 7 as my main machine. in side of VB I am running Ubuntu 10.10.

What I did was make a share folder that is transient to share C:/ that is called C_DRIVE

I then went into Ubuntu and typed in:

```
root@adam-laptop:~# mkdir /mnt/share
root@adam-laptop:~# mount.vboxsf TOA /mnt/share
mount.vboxsf: mounting failed with the error: Protocol error
```

So what am I doing wrong?

If I type in the second line, the one where I mount it, as C_DRIVE instead of share I get folder not found, obviously....

So wtf. LOL.

Help

---

### Post by Adrienk on 2010-10-22
bump

---

### Post by 3Miro on 2010-10-22
Have you installed guest addons under Ubuntu? The video driver may not work properly, since Ubuntu 10.10 uses the newer Xorg server 1.9, however, folder mounting should work.

---

### Post by sikander3786 on 2010-10-22
These might help.

[http://ubuntuforums.org/showthread.php?t=1006818](http://ubuntuforums.org/showthread.php?t=1006818)

[http://forums.virtualbox.org/viewtopic.php?f=3&t=6245](http://forums.virtualbox.org/viewtopic.php?f=3&t=6245)

---

