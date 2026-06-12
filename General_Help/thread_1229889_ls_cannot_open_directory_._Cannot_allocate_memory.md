---
title: "ls: cannot open directory .: Cannot allocate memory"
date: 2009-08-02
forum: General Help
---

### Post by cbear on 2009-08-02
I just started getting these memory errors today.  So far I have only seen them when trying to open (ls) anything in /media.  I checked my real and virtual memory and there is plenty of both available.  Any thoughts ?


ls: cannot open directory .: Cannot allocate memory

=-=-=-=-=-=-=-=-=-=-=-=-

UPDATE:  seems to be limited to a particular mount /media/tbone

I did a umount /media/tbone  and then tried to mount again:

root@LINUX03:/home/backups# . mount.tbone
mount error 12 = Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

---

