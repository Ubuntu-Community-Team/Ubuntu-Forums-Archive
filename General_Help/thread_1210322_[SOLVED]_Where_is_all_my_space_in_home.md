---
title: "[SOLVED] Where is all my space in /home?"
date: 2009-07-11
forum: General Help
---

### Post by bbbaldie on 2009-07-11
I have a separate partition for /home (25 gigs). It shows that I'm using 23 gigs. However, no matter how many files I delete, this number doesn't change. I'm showing nothing in trash.

```
rone@rone-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              71G   63G  4.3G  94% /
tmpfs                 975M     0  975M   0% /lib/init/rw
varrun                975M  360K  975M   1% /var/run
varlock               975M     0  975M   0% /var/lock
udev                  975M  180K  975M   1% /dev
tmpfs                 975M  640K  975M   1% /dev/shm
lrm                   975M  2.2M  973M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda2              25G   23G  1.6G  94% /home
/dev/sda1             205G  134G   61G  69% /mnt/250g

```

Any ideas?

---

### Post by Johnny B on 2009-07-11
did you try the disk usage analyzer?

---

### Post by Cheesemill on 2009-07-11
I'd be more worried about why my / partition was 63GB

---

### Post by Celauran on 2009-07-11
> **Cheesemill said:**
> I'd be more worried about why my / partition was 63GB

This.

To get a better idea of what's going on, check

```
sudo du -sh /*
du -sh /home/you/*
```

---

### Post by drs305 on 2009-07-11
There is a link in my signature line to a Ubuntu help wiki I wrote on finding lost free space. It tells you how to find what is taking up the lost space, how to recover it, and how to prevent it from happening again.

The most common problems are undeleted trash (check root's trash as well as your own), backups made to the wrong location (written to a system partition instead of to an external drive, for instance) and large log files.

Although you wrote about "/home", your / partition is also very full and I would check that as well unless you know you have a large amount of data stored on that partition.

---

### Post by bbbaldie on 2009-07-11
Thanks, all, for the suggestions. I guess I didn't have enough coffee this morning! The Disk Usage Analyzer revealed 17 gigs of stuff in .trash. Something was goofed with my trash emptying.:guitar:

---

### Post by bbbaldie on 2009-07-11
One last thing, on my / partition, I had a backup routine set up to copy my huge music collection to a remote server (/mnt/srv1) and the server wasn't mounted! All that stuff was duped on my hard drive!

Again, thanks, Ubuntu community!):P

---

