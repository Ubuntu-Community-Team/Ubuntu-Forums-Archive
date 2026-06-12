---
title: "chmod doesn't work"
date: 2011-06-20
forum: General Help
---

### Post by DanniN on 2011-06-20
Hi!

I'm having problems with chmodding a NTFS directory. I'm having problems accessing the directory through samba because of some missing permissions, but when I try to set them, nothing happens.

This is what I do:

```
root@proliant:/media# ls -l
total 32
lrwxrwxrwx 1 root  root       6 Jun 20 14:47 cdrom -> cdrom0
drwxr-xr-x 2 root  root    4096 Jun 20 14:47 cdrom0
drwxr-xr-x 2 root  root    4096 Jun 20 14:47 cdrom1
**drwx------ 1 danni admins  4096 Jun 18 03:29 hdd.1**
drwx------ 1 danni danni  20480 Jun 20 15:28 Pvt
root@proliant:/media# chmod -v 770 hdd.1
**mode of `hdd.1' changed to 0770 (rwxrwx---)**
root@proliant:/media# ls -l
total 32
lrwxrwxrwx 1 root  root       6 Jun 20 14:47 cdrom -> cdrom0
drwxr-xr-x 2 root  root    4096 Jun 20 14:47 cdrom0
drwxr-xr-x 2 root  root    4096 Jun 20 14:47 cdrom1
**drwx------ 1 danni admins  4096 Jun 18 03:29 hdd.1**
drwx------ 1 danni danni  20480 Jun 20 15:28 Pvt
```

(I have highlighted the lines of most relevance)

I also tried to replace 'hdd.1' with '/media/hdd.1' and 'hdd.1/'

Any ideas or help would be gratefully appreciated!

---

### Post by hwttdz on 2011-06-20
There are two possibilities:
1) more likely, that you have the mount options wrong, I think that the permissions there will be set at mount time, possibly in one of the masks.  Anyways, first place I'd look would be mount options.
2) less likely, something is going wrong in the very strange alternate universe which is ntfs to linux permissions conversions.  This site has a bit of information on the front: [http://b.andre.pagesperso-orange.fr/permissions.html](http://b.andre.pagesperso-orange.fr/permissions.html)

---

### Post by idoitprone on 2011-06-20
ntfs and fat do not understand linux file permissions

ntfs permissions are determined at mount

you cannot chmod or chown once ntfs is mounted

---

