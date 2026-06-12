---
title: "External drives don't mount properly without Gnome"
date: 2011-04-18
forum: General Help
---

### Post by davidfeldman on 2011-04-18
I'm running Ubuntu 10.10 on a Zotac nettop. When I boot up normally, all my external USB drives are recognized and mounted properly in /media. 

But when I boot up without Gnome (i.e. there's no monitor attached so Gnome doesn't start) they don't mount right: I see directories for them inside /media but normal users don't have access, and root only sees an empty directory.

Any idea what's happening and, more importantly, how to fix it?

---

### Post by wolfen69 on 2011-04-18
Have you tried mounting them with
```
sudo mount /dev/sda1
```
sda1 being just an example of a drive you want mounted.
To see a list of all your devices do
```
sudo fdisk -l
```

---

### Post by davidfeldman on 2011-04-18
I have to supply a mount point manually, e.g. "sudo mount /dev/whatever /media/whatever" but yes that works.

But when I start up with the monitor connected (i.e. Gnome starts up), connected drives just automount with appropriate names in /media. I'd like that to happen when the machine is headless too.

---

