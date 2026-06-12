---
title: "mount permissions."
date: 2010-03-20
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-03-20
how do i give group write permissions in fstab?

i'm trying to mount a virtualbox shared folder.


currently my fstab looks like this


```
Share_Name /mnt/point vboxsf rw,uid=1000,gid=1000 0 0
```


i want to give both the owner and group, write permissions. currently, only the owner has write permissions, and group read with these mount options.


Thanks.

---

### Post by zvacet on 2010-03-21
Try [this.]("http://ubuntuforums.org/showthread.php?t=872197")

---

### Post by NiGhtMarEs0nWax on 2010-03-21
Thanks for the reply, it seems that mounting virtualbox shares are slightly different from mounting Linux volumes.

what was required was:

```
Share_Name /mnt/point vboxsf uid=1000,gid=100,dmode=770,fmode=770 0 0
```

that will set the group to 'users' and allow full permissions to group + owner, and none to others.

Thanks.

---

### Post by teohhanhui on 2010-04-30
> **NiGhtMarEs0nWax said:**
> Thanks for the reply, it seems that mounting virtualbox shares are slightly different from mounting Linux volumes.

what was required was:

```
Share_Name /mnt/point vboxsf uid=1000,gid=100,dmode=770,fmode=770 0 0
```

that will set the group to 'users' and allow full permissions to group + owner, and none to others.

Thanks.

Thanks! They should've mentioned this in the VirtualBox manual.

---

