---
title: "/ getting filled up every night"
date: 2010-06-18
forum: General Help
---

### Post by belfasttim on 2010-06-18
Hi-- 

I've been running Ubuntu 9.1 for about a year or so with no issues.

Lately however my root filesystem is getting filled up every night-- I come in in the morning and have notices that I have 0 bytes remaining. There's tons of room on the disk, but the root is full. 

Here's what it looks like with a df -h:

```
me@my-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              58G   58G     0 100% /
udev                  3.8G  240K  3.8G   1% /dev
none                  3.8G  188K  3.8G   1% /dev/shm
none                  3.8G  232K  3.8G   1% /var/run
none                  3.8G     0  3.8G   0% /var/lock
none                  3.8G     0  3.8G   0% /lib/init/rw
/dev/sda1             382G   12G  351G   4% /home
```

I suspect I've got my partitions messed up from the install-- can anyone point out what I've got wrong and how to fix it?

Thanks!

---

### Post by d3v1150m471c on 2010-06-18
filled up with what or by what is the question... have you checked running processes?

---

### Post by dtfinch on 2010-06-18
Are there any huge files, like in /var/log? Last time one of our servers filled up unexpectedly, Openfire (xmpp messaging server) had gotten stuck in a infinite loop writing errors to one of its logs.

If you find such a file, deleting it might not be enough. If a program still has the file open, even if it's deleted, it'll continue to use space until the file's closed.

---

### Post by jerome1232 on 2010-06-18
```
sudo du -hx --max-depth=1 /
```

That will give you a start, I suspect you have a backup running to /var (simple backup? I think it's called) But that's just a suspicion, let's see what's going on.

---

### Post by belfasttim on 2010-06-18
> **jerome1232 said:**
> ```
sudo du -hx --max-depth=1 /
```

That will give you a start, I suspect you have a backup running to /var (simple backup? I think it's called) But that's just a suspicion, let's see what's going on.


Thanks guys-- Jerome, you're exactly right! I did install simplebackup, and it is eating up my /var dir. 

That saves me.

Thanks a lot for your help.

---

