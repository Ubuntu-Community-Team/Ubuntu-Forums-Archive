---
title: "Mounting ntfs drive with trash enabled in multi-user setup"
date: 2010-06-07
forum: General Help
---

### Post by krippa on 2010-06-07
I'm currently setting up a multi-user laptop for a friend and just when I thought everything was good to go I noticed that the ntfs partitions are mounted fine but without support for trash. Apart from meaning that a pretty important feature would not be there, it is really annoying not being able to delete photos from within the image-viewer, it just complains without giving an option to delete completely.

I tried some solutions in threads here on the forum but they seemed to address only the single-user case and "solved" the problem by allowing one user complete access (including to trash) and left other users unable to even mount the drive.

Is there any way to solve or work around this? It's ok if this will create separate trash folders for all users (.Trash-1000, .Trash-1001 etc.), as long as it works...

Thanks,
Kris

p.s. I tried these fstab entries:

```

#Works for user 1000 but leaves everyone else without access
UUID=9CBC8F21BC8EF4D4 /media/Windows  ntfs    defaults,nls=utf8,umask=007,uid=1000 0       0
#As close to default setup I get, all members of "users" can use the drive though only root can move to trash
UUID=008A20B18A20A4DE /media/Arquivos ntfs    defaults,nls=utf8,umask=007,users,gid=users 0       0

```

---

