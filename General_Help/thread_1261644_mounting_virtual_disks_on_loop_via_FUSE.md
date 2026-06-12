---
title: "mounting virtual disks on loop via FUSE"
date: 2009-09-09
forum: General Help
---

### Post by John Baptist on 2009-09-09
Hi. So, my understanding is the FUSE should allow me to mount file systems in userspace (that is, without resorting to sudo). What I'd like to do is to be able to create and mount a virtual disk without ever becominng root. 

Normally, I do something like this:

```

dd if=/dev/zero of=my.disk bs=1M count=1000
mkdir my.mountpoint
sudo mount -o loop ~/my.disk ~/my.mountpoint

```

That works fine. How can I do this using fuse, and bypass the sudo? I'd like to be able to have virtual disks "automagically" mounted from Gnome, and put in my ~/.gvfs directory. I've tried stuff like this:

```

gnome-mount -v -b -o loop -d ~/my.disk
fusermount -o loop ~/my.disk
gvfs-mount file:///home/myuser/my.disk

```

Anyway, none of this worked, and each command gave cryptic messages and they are all poorly documented. I've Googled "ubuntu loopback fuse mount" and so forth in several varieties.

So, my questions:
1. Does anyone know how to do this?
2. If you don't, do you know if it's possible?
3. If it's not possible, SHOULD it be possible?

Thanks for your help in advance.

---

### Post by avdd on 2011-07-06
I am looking for an answer to this too.  How can I bump this thread?

---

