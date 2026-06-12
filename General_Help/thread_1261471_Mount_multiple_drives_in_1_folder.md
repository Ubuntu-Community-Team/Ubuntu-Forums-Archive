---
title: "Mount multiple drives in 1 folder"
date: 2009-09-08
forum: General Help
---

### Post by readycarpenter on 2009-09-08
I read [COLOR="Blue"][this]("http://ubuntuforums.org/showthread.php?t=120378") [/COLOR]post and it was not helpful for what I wanted to do. 

 so I created this post to show how to mount multiple different file systems into one folder, using "mhddfs" (Multi-hdd FUSE filesystem).

 I do this to combine all my movies into one samba share directory for other lan users and my htpc to access. this is safer than raid jbod, as if one drive fails the data is still accessible on the other drives.

here are some fstab examples:

```
#first mount the samba shares vol1, vol2, and newmovies
//htpc/vol1  /mnt/vol1  cifs  user=user,pass=pass,uid=1000,gid=100  0  0
//htpc/vol2  /mnt/vol2  cifs  user=user,pass=pass,uid=1000,gid=100  0  0
//desktop/newmovies  /mnt/newmovies  cifs  user=user,pass=pass,uid=1000,gid=100  0  0

#then mount vol1 vol2 and newmovies to one directory
mhddfs#/mnt/vol1,/mnt/vol2,/mnt/newmovies ~/Videos/Movies fuse defaults,allow_other 0 0
```

---

