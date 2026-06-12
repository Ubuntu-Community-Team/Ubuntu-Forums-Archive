---
title: "How to run fsck?"
date: 2010-06-12
forum: General Help
---

### Post by oxf on 2010-06-12
OK its not a good idea to run fsck on a mounted file system.
But.. if I want to check the file system between the default checks on boot up how should I safely do it? How do I safely run fsck?
Thanks

---

### Post by oldfred on 2010-06-12
Must be unmounted:
Try "e2fsck -f /dev/sdb2". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by oxf on 2010-06-12
> **oldfred said:**
> Must be unmounted:
Try "e2fsck -f /dev/sdb2". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

OK thanks, so I boot from the live CD. So there's no safe way to do it otherwise then, like recovery mode?

---

### Post by quadproc on 2010-06-12
> **oxf said:**
> OK its not a good idea to run fsck on a mounted file system.
But.. if I want to check the file system between the default checks on boot up how should I safely do it? How do I safely run fsck?
Thanks
If you can mount the disk in question as read-only then you run fsck on it.  But a system disk cannot be run read-only; lots of stuff gets written to it and you can't control most of those things: locks and logs and /tmp come to mind.

The safe way to do fsck is to run from a different device than what you want to check.  Live CD, removable hard disk, USB flash drive are some possibilities.

quadproc

---

### Post by Morbius1 on 2010-06-12
You can force a check of your root filesystem by issuing the following command in a terminal and rebooting:

```
sudo touch /forcefsck
```

[COLOR=Blue]EDIT: Sorry I should have noted that this will also reset the 30-mount count. [/COLOR]

---

### Post by oxf on 2010-06-12
OK thanks all!
So I could also add -c to the forced check?
i.e  /forcefsck -c

---

### Post by Morbius1 on 2010-06-12
> **oxf said:**
> So I could also add -c to the forced check?
i.e  /forcefsck -c

I have never used that option with /forcefsck nor have I ever seen that in any documentation. So If I had to wager my money I would say, no. The only thing that touch /forcefsck is doing is creating a file.

---

### Post by oxf on 2010-06-12
> **Morbius1 said:**
> I have never used that option with /forcefsck nor have I ever seen that in any documentation. So If I had to wager my money I would say, no.

OK. I used it when I couldn't mount the file system but maybe not from force then
thanks..

---

### Post by rtimai on 2010-06-12
This might be a cop-out, but...
fsck --help
man fsck
  q to quit. I always forget...

---

