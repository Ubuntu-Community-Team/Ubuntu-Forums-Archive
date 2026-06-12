---
title: "Cannot unmount volume (CD/DVD RW)"
date: 2009-10-11
forum: General Help
---

### Post by cguy on 2009-10-11
Many times when I want to eject a DVD/CD I get the following error message:

Cannot unmount volume
Details:
umount: only root can unmount /dev/scd0 from /media/cdrom0

The fstab entry is
/dev/scd0 /media/cdrom0 udf,iso9660 user,auto,exec,utf8 0 0

Ideas on how to fix this?

(Jaunty, Gnome)

---

### Post by mac9416 on 2009-10-11
This has always worked for me ([http://ubuntulinuxhelp.com/quick-tip-when-linux-wont-give-your-cd-back/](http://ubuntulinuxhelp.com/quick-tip-when-linux-wont-give-your-cd-back/)):

```
$ sudo umount /media/cdrom0/ -l
```

---

### Post by cguy on 2009-10-11
I know that, but it's annoying, cumbersome and it's not how things are meant to be. Is that the only workaround the bug?

---

### Post by mac9416 on 2009-10-11
That is the only fix I know of. And that blogger says it's not a bug, though you're right, it certainly shouldn't be that way.

Thanks for the heads-up about the link. Fixed it.

Sorry I can't be any more help.

---

### Post by cguy on 2009-10-11
Whoa, new threads get buried so fast here :D

---

