---
title: "Ubuntu Sees External Drive but No Space"
date: 2009-08-05
forum: General Help
---

### Post by CarlosinFL on 2009-08-05
When I connect my USB external hard drive to my PC, Ubuntu quickly recognizes it and then I see that it only shows I have 180 MB's of disk space available. This is crazy to me since I know the folder is empty. I checked to make sure /dev/sdg1 is properly mounted to /media/disk and it is however I then can't find anything in the directory doing an 'ls -la'.

```
/dev/sdg1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

root@tunafish:/media/disk# pwd
/media/disk
root@tunafish:/media/disk# ls -la
total 20
drwx------ 2 cwilliams root 16384 2009-08-05 12:11 .
drwxr-xr-x 5 root      root  4096 2009-08-05 10:43 ..
```

What can I do to understand why my disk wont be recognized as 250 GB as it should...

---

