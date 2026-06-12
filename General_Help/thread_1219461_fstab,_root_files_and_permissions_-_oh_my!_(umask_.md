---
title: "fstab, root files and permissions - oh my! (umask on ext3 problem)"
date: 2009-07-21
forum: General Help
---

### Post by dmstudios on 2009-07-21
So, I have a 2nd hdd in my linux box that used to be vfat. File permissions weren't ever a problem because I had configured the drive in my fstab with umask=002 and guid=username, like so:

```

/dev/sdb1   /media/datadisk   ext3   defaults,umask=002,uid=designmagic   0   0

```That worked perfectly.

Now, I've formatted it to ext3 and whenever I run Photoshop in VirtualBox I can't save any files on the drive. It gives me an error saying 'the file is locked.'

It's because when I go to save the file, a new file (named something like ~ps1.tmp) is created and it only has read permissions.

So, my question is how can I make all new files that are created by VirtualBox (root I assume?) have the same permissions as my normal user? 

umask does not work on ext3, but I need that feature! 

Thanks in advance for any insight you might give on this issue.

---

### Post by dmstudios on 2009-07-21
Oh, some more info that you want..

- I have changed the owner of the mount point (/media/datadisk) to myself.

- I have run : chmod -R 777 /media/datadisk (the mount point)

---

