---
title: "Ntfs Partition Permissions?!"
date: 2006-03-28
forum: General Help
---

### Post by immerohnegott on 2006-03-28
OK, I've been able to mount both of my NTFS parts, however, since they must be mounted as root, root is the only user allowed to read the disks...i am a bit of a newbie to the OS and therefore have no idea how to automount these partitions at boot so that they can be read by all users...

hilf mir bitte!


auf wiedersehen, 
--Ray

---

### Post by japs_it88 on 2006-03-28
you have to edit your /etc/fstab file
```
sudo gedit /etc/fstab
```

for the ntfs patition you are interested in, change the "option" colomn from "defaults" to "umask=0222"
this is what it looks like for me

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda1       /media/sda1     ntfs   umask=0222    0       0
```

---

### Post by duelboot on 2006-03-28
Japs posted the above as I was typing...removing my info as it is redundant.
duel

---

### Post by immerohnegott on 2006-03-28
thanks a bundle...i had tried using the 'umask=0222' phrase in the mount command, but it never worked properly...OTS error i suppose (operator too stupid)......

---

