---
title: "Problems mounting samba share"
date: 2012-07-21
forum: General Help
---

### Post by ender8282 on 2012-07-21
OK so I've got two samba shares that I'm trying to get mounted.  Both are being shared from the same Windows 7 machine.  One mounts with out problems, the other one complains about permission denied.  

$ sudo mount -t cifs //WIN-PC/BD-Documents ./docs -o guest
$ sudo mount -t cifs //WIN-PC/BD-Media ./media -o guest
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
$ mount | grep WIN
//WIN-PC/BD-Documents on /home/jhubbard/mnt/docs type cifs (rw,mand)

It does not matter which share I attempt to mount first.  It isn't a permission problem on the Linux directory side (i.e. I can mount BD-Documents to ./media).  I've poked around on the windows side and there don't appear to be any differences between the shares.  I don't have any problems accessing either share from a different Windows 7 pc. 

Any thought would be appreciated.

---

