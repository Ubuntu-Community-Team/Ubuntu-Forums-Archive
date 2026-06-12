---
title: "Changing mount options w/o rebooting?"
date: 2009-08-01
forum: General Help
---

### Post by shaggy999 on 2009-08-01
I'm having some trouble getting a program to install because I have /tmp mounted to tmpfs w/ noexec and an install script is extracting a script to /tmp and attempting to run it. Is there a way to get the system to remount /tmp with exec enabled temporarily without having to change fstab, reboot, install, change fstab, reboot?

I am wary of just simply unmount /tmp manually because programs write stuff to there and it will disappear when I unmount and I don't want programs to crash.

---

### Post by kidders on 2009-08-02
Hi there,

Check out mount's "remount" option ... it should do the trick.

In general, rebooting is not required to change a filesystem's mount options. All you should normally need to do is apply your changes & update /etc/fstab (if desired).

If you run into trouble, you could always go the long way round, and do something like this...```
lsof | grep /tmp  (Check nothing is using /tmp right now)
cp -dpR /tmp /tmp2
umount /tmp
```
Then, you could re-create /tmp however you want & copy all the files back in, just in case anything might be surprised to see them vanish.

I hope that helps.

---

