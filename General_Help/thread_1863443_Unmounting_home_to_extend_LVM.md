---
title: "Unmounting /home to extend LVM"
date: 2011-10-17
forum: General Help
---

### Post by Enforcer83 on 2011-10-17
I have an LVM to which the home directories of my system reside.  I am attempting to extend the LVM to another harddrive.  Following the Ubuntu Server guide, I attempted to unmount the /home and got the following error:

```

$ sudo umount /home
umount: /home: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

umount -f gives the following:

```
$ sudo umount -f /home
umount2: Device or resource busy
umount: /home: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy
```

How can I finish the resizing and check of the LVM filesystem properly?

Do I need to use a LIVE CD?  If so a "How To" would be helpful.

---

