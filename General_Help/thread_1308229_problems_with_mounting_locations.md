---
title: "problems with mounting locations"
date: 2009-10-31
forum: General Help
---

### Post by mimoza on 2009-10-31
I have erased my slave hard disc (which was ext3) and made it ntfs. And now, when I'm trying to mount it via nautilus it says:
"Unable to mount location
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/HD2"

So I tried to mount it via terminal, in root by "mount /dev/sdb1" (which is it), but then I got:

```
mount: /dev/sdb1 already mounted or /media/HD2 busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/HD2
```("/media/HD" was a mounting location for that hard disc before, while it was ext3)

...and it disappeared from nautilus.

In GParted it says that my hard disc has got 4 mounting locations ("/media/HD2", "/media/HD2", "/media/HD2" and "/mnt/HD" -????) and that it isn't mounted. So I mount it on one of it ("/media/HD2") and I can't access it. I get:
"The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "HD2"."

...so I try to change the owner by "chown 777 /media/HD2", and I get

```
chown: changing ownership of `/media/HD2': Read-only file system
```...and I feel even more confused. I am a total beginner and I really don't know what to do now. :(

What I want, is to have one mounting location ("/media/HD2") and that every account on my computer can access it.

Thanks in advantage.

---

### Post by mimoza on 2009-10-31
now I unmounted it again and erased all mounting locations ("/media/HD2" and "/mnt/HD2").
And now it appears in "computer:///" (nautilus) and I can't mount it.
...help?

---

