---
title: "General question regarding mount."
date: 2011-01-14
forum: General Help
---

### Post by MrWestwood on 2011-01-14
How do I go about mounting a device if I don't know the file system type (e.g ext3, NTFS)?

---

### Post by drewsus on 2011-01-14
you need to be way more specific than that, but usually plug it in and it will automount.

---

### Post by WorMzy on 2011-01-14
If you don't specify a filesystem, mount will use the information available about the partition and try to use the correct filesystem.

e.g. if I run

```
sudo mount /dev/sdc3 /mnt
```

it will mount it (my Windows Vista partition) as ntfs-3g.

if I run

```
sudo mount /dev/sdc7 /mnt 
```

it will mount it (my Debian partition) as ext3.

---

### Post by sisco311 on 2011-01-14
Usually, mount recognizes the file system type, so you don't have to specify it.

You can use **fdisk** and/or **blkid** to get the type of the filesystem.

See:
```
man mount | less +/"If  no  -t  option is given"
```

---

### Post by MrWestwood on 2011-01-14
Thanks guys. I was certain I heard that the correct procedure was to specify the file system. 

Thanks for your help.

---

