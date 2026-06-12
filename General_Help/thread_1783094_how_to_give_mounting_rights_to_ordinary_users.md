---
title: "how to give mounting rights to ordinary users?"
date: 2011-06-15
forum: General Help
---

### Post by apoorvmunshi on 2011-06-15
I am posting the o/p of /etc/fstab and /etc/mtab...Currently i am the only user but if i add one more , how can i give that user the right to mount any partition ??

---

### Post by apoorvmunshi on 2011-06-15
this is the o/p ..

---

### Post by seawolf167 on 2011-06-15
You should take a look at [RootSudo]("https://help.ubuntu.com/community/RootSudo"). When you edit your /etc/fstab file, you'll have to use *sudo*, like below

```
gksu gedit /etc/fstab
```Once you add the entry in /etc/fstab, the drive will be automatically mounted and you won't have to worry about mounting it again.

---

### Post by pqwoerituytrueiwoq on 2011-06-15
in the column where you could but default add user
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by apoorvmunshi on 2011-06-15
ya i have enabled automounting ... so if i create another user , will he be able to access that drive??

---

### Post by seawolf167 on 2011-06-15
> **apoorvmunshi said:**
> ya i have enabled automounting ... so if i create another user , will he be able to access that drive??

Provided you set your permissions correctly, yes. Take a look [here ]("https://help.ubuntu.com/community/FilePermissions")for more file permission info.

---

### Post by pqwoerituytrueiwoq on 2011-06-15
> **apoorvmunshi said:**
> ya i have enabled automounting ... so if i create another user , will he be able to access that drive??
one way to find out use a guest session

---

### Post by WorMzy on 2011-06-15
If you add the new user to the admin group, they should be able to use sudo. To let them mount partitions manually through nautilus, you may need to add them to the optical and/or storage groups. I'm not sure how Ubuntu handles this these days.

If you add another user, you'll find that they can't write to the NTFS partition. They'll still be able to read and execute, but they won't be able to create new files or delete old ones.

One way around this is to create a new group, and add to it the users you want to be able to access the partition; then use that group's ID in the gid argument under options.

e.g.
Create a new group with the id of 1050, and add users Frank, James and Lisa to it. Then modify fstab so that the mount line looks like this:
```
/dev/sda6 /media/apoorv ntfs-3g auto,uid=1000,**gid=1050**,umask=002 0 0
```

Then when the partition is mounted, Frank, James and Lisa will have Read, Write and Execute permissions on that filesystem.


Alternatively, you could just give *everyone* those permissions by changing the umask value to 000. This method is easier, but a lot less secure.

---

