---
title: "terminal mount command problem"
date: 2011-11-27
forum: General Help
---

### Post by begin on 2011-11-27
Well  I have .raw image and want to mount it as loopback device 
as shown in this [thread]("http://www.turnkeylinux.org/blog/convert-vm-iso")
so the problem when I type 
mount -o loop filename.raw filename.mount
It says you need to specify file system first and I tried many syntax but it didn't work
so i need the right syntax to do this

---

### Post by blueridgedog on 2011-11-27
The syntax from the man page of mount is:

```
mount /tmp/disk.img /mnt -o loop
```

So try:

```
mount /path/to/filename.raw /path/to/filename.mount -o loop
```

If it fails, please copy and paste the error.

---

