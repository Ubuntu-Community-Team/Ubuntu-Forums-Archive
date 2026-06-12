---
title: "Boot fsck doesn't finish, then drive doesn't mount."
date: 2010-03-04
forum: General Help
---

### Post by Giggity on 2010-03-04
The strangest thing has been happening for the past few days.  I boot my system after an update, fsck starts and flickers on the splash screen for a couple seconds, but it doesn't finish.  This is strange enough, but when I log into my desktop, I find that the drive fsck was supposed to check isn't mounted.

I've tried unsuccessfully to mount the drive in the terminal, but it's not working.

```
***@***-desktop:~$ sudo mount /dev/sdc1 /media/sdc1
mount: /dev/sdc1 already mounted or /media/sdc1 busy
***@***-desktop:~$ sudo umount /dev/sdc1
umount: /dev/sdc1: not mounted
```Anyone have an idea?  I don't even know where to start.

---

### Post by Tuxi on 2010-03-04
Will it mount if you give the fsck time to finish?  I had that problem at one time, and it automounted a few minutes after starting.

---

### Post by Giggity on 2010-03-04
Yeah, it eventually mounted itself after about 45 minutes.  On one hand this is a cool feature because it lets me do the automatic boot-time fsck without being locked out of the desktop.  Just didn't know that's what was happening.

Thanks for your help!

---

