---
title: "rsync not skipping unchanged files.."
date: 2010-03-01
forum: General Help
---

### Post by switch10 on 2010-03-01
I am running this command,
```
 rsync -vrl --progress --stats --perms --delete --exclude '*~' --exclude 'Music' --exclude 'server' --exclude 'Downloads' --exclude 'Ubuntu One' --exclude 'Videos' /home/dave/ /media/server/backup/desktop/dave 
```

It transfers files that remain unchanged.  The one that I notice every time is ```
.VirtualBox/HardDisks/anOS.vdi
```
I have several OSes installed in VirtualBox, so this takes a very long time.

What am I doing wrong?

---

### Post by switch10 on 2010-03-01
ok, apparent;y the problem is with VirtualBox disk images only.  When you run a system on a disk image, there is not only new data appending to the end of the file, but the entire disk image is changing.  That is why rsync is backing up the entire file.

My solution to this, was to add --exclude '.VirtualBox'

---

