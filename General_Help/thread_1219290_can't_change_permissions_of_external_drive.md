---
title: "can't change permissions of external drive"
date: 2009-07-21
forum: General Help
---

### Post by styleruk on 2009-07-21
A tad confused here.  I have an external drive with pic, files and music on it.  It's always been a shared drive across the network.  I've upgraded to 9.04 64bit, I was 8.10 64bit before and have no problem mounting the drive and accessing the folders but can't write to them!
I've tried the command;
sudo chown -R simon:simon /media/SHARED

but it lists loads of errors trying, no permission etc...

If I 'sudo nautilus', I can write to it but can't change the permissions in nautilus as root.  It just changes back.
I have this entry in my fstab:

/dev/sdi1 /media/SHARED vfat defaults 0 0



Any advice?

Si

---

### Post by drs305 on 2009-07-21
You can't change permissions on a non-linux partition once it is mounted. You change them at the time of mounting.

To change ownership, in the fstab file change the options to include your uid (normally 1000 for the first user):
```

/dev/sdi1 /media/SHARED vfat uid=1000,umask=022 0 0

```

You can include a group id as well (gid). 

Here is a good fstab link:
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by styleruk on 2009-07-21
OK, I'll give that a go in a while and let you know.  Thanks for quick response.

Si

---

### Post by styleruk on 2009-07-22
DRS305, Thanks for your help, that worked a treat.

Si

---

