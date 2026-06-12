---
title: "Backing up"
date: 2006-06-23
forum: General Help
---

### Post by jethro10 on 2006-06-23
Hi, looking for backing up data and getting no-where.
I have my wifes windows PC, my, Ubuntu and a NAS disk at home, that can run as an FTP device as well as windows shares (samba)

On windows, theres tons of easy to use sync sotware for her data. But i'm struggling on ubuntu.

Tried sbackup as the NAS can do ftp, but it seems to prepare an archive but wont copy it up automatically even though the 'test connection' button does not give an error. The other problem with this is it needs at least as much disk space free to prepare the archive.

Looked at doing a script to copy, but the shell cant seem to give me access to samba shares, I can just get them through nautilus.

So i'm sorta getting stuck. I need it to be easy to use and hopefully GUI for the wife to use.

Any ideas?
Jeff

---

### Post by jethro10 on 2006-06-23
Well, 
I seem to have found Konserver, for KDE (ok it workds with Gnome), nice graphical front end and a basic scheduler, copies to ftp - so looks good.
and Mirrordir, a commandline product to copy to ftp.

But still no luck on a native gnome ftp or samba product.

I find this quite a bit that KDE offers superior products. A shame.

Jeff

---

### Post by aysiu on 2006-06-23
You might want to look into KDar (yes, another KDE application), Keep (also KDE), or *rsync*.

---

