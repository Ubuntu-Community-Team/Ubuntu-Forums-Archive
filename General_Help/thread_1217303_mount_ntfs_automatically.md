---
title: "mount ntfs automatically"
date: 2009-07-19
forum: General Help
---

### Post by Vishnu V on 2009-07-19
hi
I want to mount windows drives automatically.
For that i do following things
 
created a folder named windows on /media/
then in startup appliction  i created a new application with command
 
mount /dev/sda3  /media/windows
 
but it doesnt works properly
 
please help me
Thanx

---

### Post by Mazin on 2009-07-19
Filesystems that you want to have mounted automatically should be listed in your /etc/fstab file along with all the other automatic mounts.

For example, add something like:

```
/dev/sda1	/media/windows	ntfs	force,defaults,users,gid=1000,uid=1000,umask=002	0	1
```

---

### Post by Fox Dark Master on 2009-07-19
well you can always go to the add / remove programs and search on all packages for ntfs, it's probably the first aplication.

Run it and give a name to your ntfs drives and you're done :) it'll always load your drives on startup

---

### Post by oarion7 on 2009-07-19
I do this too. no need to make an auto-mount script

line from my fstab:

```
/dev/sda1       /media/disk ntfs defaults 0 0
```

---

### Post by Vishnu V on 2009-07-20
Ok Thanx my problem get solved.
May i know why the command in startup program that i created (mount /dev/sda3/ /media/windows) doesn't work properly

---

### Post by oarion7 on 2009-07-31
> **Vishnu V said:**
> Ok Thanx my problem get solved.
May i know why the command in startup program that i created (mount /dev/sda3/ /media/windows) doesn't work properly

I think because you need to be root/sudo to mount.

---

### Post by merlinus on 2009-07-31
You also need to specify the filesystem.

For example

```
sudo mount -t ntfs /dev/sda1 /media/sda1
```

---

