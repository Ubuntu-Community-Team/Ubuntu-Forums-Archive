---
title: "Find mount point by given UUID"
date: 2009-12-16
forum: General Help
---

### Post by nieproszenieja on 2009-12-16
I'm writing a small backup script.

This script should mount partition of my BACKUP-drive by given UUID, but it should first assure, whether partition isn't already mounted.
If so, it should fetch its mount point.

I know that it can be done like this:
```
#!/bin/bash
SOURCE="/media/src_partition/"
DEVICE=`blkid -U "ade25743-893b-4500-8b23-2980ebd4aeb6"`

if [ $DEVICE ]
then
  echo "Is nonzero string"
  DESTMOUNTPOINT=`mount | grep $DEVICE | gawk '{ print $3 }'`
  # Alternatively
  # DESTMOUNTPOINT=`grep $DEVICE /proc/mounts | gawk '{ print $3 }'`
  echo $DESTMOUNTPOINT
else
  echo "Is zero string"
  DESTMOUNTPOINT=/media/dest_partition
  sudo mount $DEVICE $DESTMOUNTPOINT
fi

rsync -av $SOURCE $DESTMOUNTPOINT
```

but I think it _must_ (or at least _should_) exist some native command, which make it easier, e.g:

```

mount_command -I "DEVICE-UUID"
#and also
mount_command -i /dev/sdX1

```

and it returns a mount point.

So, does enybody knows such command?

Regards,
Mateusz

P.S. If such command not exists, according to source code of mount command I'm pretty sure, that's easy to implement.

---

### Post by nieproszenieja on 2009-12-18
I've found a workaround for mounting device on demand by given uuid - autofs/automount/automounter allow to mount device by given UUID.

So my auto.misc is:
```
black2 -fstype=auto UUID="beef9003-7011-46bd-9471-0b6a71bdc68b"
black3 -fstype=auto UUID="53F018DA89032092"
black5 -fstype=auto UUID="4b792c9a-ed76-4161-bc1e-920286726a17"
black6 -fstype=auto UUID="ade25743-893b-4500-8b23-2980ebd4aeb6"
```

But my first question is still up to date: **does enybody knows tool, which is able to return mount point by given UUID (or block device)?**

---

### Post by petteriIII on 2009-12-18
> **nieproszenieja said:**
> I've found a workaround for mounting device on demand by given uuid - autofs/automount/automounter allow to mount device by given UUID.

So my auto.misc is:
```
black2 -fstype=auto UUID="beef9003-7011-46bd-9471-0b6a71bdc68b"
black3 -fstype=auto UUID="53F018DA89032092"
black5 -fstype=auto UUID="4b792c9a-ed76-4161-bc1e-920286726a17"
black6 -fstype=auto UUID="ade25743-893b-4500-8b23-2980ebd4aeb6"
```

But my first question is still up to date: **does enybody knows tool, which is able to return mount point by given UUID (or block device)?**

 
If I understood you, you answered your question by yourself: mount | grep `blkid -U beef9003-7011-46bd-9471-0b6a71bdc68b` | awk '{ print $3 }'

---

### Post by nieproszenieja on 2009-12-18
Partially yes, but I wrote also:

"**I think it _must_ (or at least _should_) exist some native command, which make it easier, e.g:**
```
mount_command -I "DEVICE-UUID"
#and also
mount_command -i /dev/sdX1
```

There are tons of post about "finding device mount point", but I never found an answer, that this can be done more elegant and easier (I can't believe, that souch easier solutions doesn't exist).

---

