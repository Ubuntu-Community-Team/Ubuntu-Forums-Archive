---
title: "Mounting a hard disk permanently"
date: 2011-09-25
forum: General Help
---

### Post by kingfisher_ph on 2011-09-25
Hello everybody!
I'm new in ubuntu 11.04! As a result, I have a definitely dump question!! ):P That's how to mount a hard disk permanently!!! Is there any way to do that??
Yeah! I  just make some "link_to folders" in a not system disk!  Then i put it in my desktop! Every time i reboot my desktop, I can't use those link_to forders anymore!! To use them, i have to mount the hard disk again!! Of course, it's not a convenient way!
Therefore, I want to mount a certain harddisk permanently, and i don't have to mount it again each time i reboot!!
Somebody help me??? Thank you all very much!!!

---

### Post by docbop on 2011-09-25
Read the man page for the fstab file in /etc.  That is what is read to know what filesystems to mount.  Be sure to make a backup of your fstab before you start changing it so you can always get back if something goes wrong.

---

### Post by dave01945 on 2011-09-25
also after editing **fstab** if you run 

```
sudo mount -a
```

that should give you any error messages if there is a problem it's often easier to find before you reboot because it may not reboot if it is wrong

---

### Post by oldos2er on 2011-09-25
> **kingfisher_ph said:**
>  I have a definitely dump question!! ):P That's how to mount a hard disk permanently!!! Is there any way to do that??

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

