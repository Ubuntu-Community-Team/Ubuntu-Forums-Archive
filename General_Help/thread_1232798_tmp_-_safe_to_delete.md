---
title: "/tmp - safe to delete?"
date: 2009-08-05
forum: General Help
---

### Post by kg84 on 2009-08-05
Hi guys...

Is it safe to delete everything in /tmp? I dont have much there - am just curious - have noticed there are a couple of files ('ATI*") owned by root.

:)

---

### Post by 3rdalbum on 2009-08-06
It's safer to leave them there. They are deleted on bootup anyway.

---

### Post by kg84 on 2009-08-06
> **3rdalbum said:**
> It's safer to leave them there. They are deleted on bootup anyway.

Ahhh - OK, didn't know that.

Cheers.

---

### Post by lensman3 on 2009-08-06
I think you can do a rm on /tmp. If you can't delete a file, then the OS won't delete it.  Even if the file is in use.  Try it and see.  The worse that can happen you won't be able to login.  Then just do a reboot to fix it.

It is possible to delete an open file (as root) and the name will disappear.  Except the usage count on the file won't go to zero.  If the useage count is zero, then the kernel will finally delete it.

That is why it is called tmp, everything in the directory is supposed to be deleted by the OS during boot.   My machine stays on 24/7 so occasionally I go through it and delete stuff and I haven't killed my system yet.  Don't delete "lost+found" if it exists, as it keeps track of bad sectors on your disk (or at least it use to).  Every partition has a lost+found directory.

---

### Post by kg84 on 2009-08-06
Thanks lensman3  My /tmp folder is currently at 28kb in size, so no issue here with it taking up too much space :)  My machine normally stays on for a couple of days before being rebooted, so for now, whilst I am busy studying/learning I'll leave the /tmp folder alone. Thanks also for the explanation regarding lost and found - I was only wondering about this last night.  :)

---

