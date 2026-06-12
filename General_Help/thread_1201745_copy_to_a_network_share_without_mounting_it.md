---
title: "copy to a network share without mounting it"
date: 2009-07-01
forum: General Help
---

### Post by ridshack on 2009-07-01
Yo Ubuntonians,

I backup my linux box to a smb or nfs share. I have the share mounted in /mnt/mybackupdir and at some point in time since these servers rarely get rebooted the mounted share is no longer valid. Then everything is backed up local and not to my share and I may not know until a month or more when I happen to catch it )-:

What are some of the solutions you use to overcome this issue?

Can I copy direct to a network share without mounting it? Both smb and nfs?

---

### Post by schilcha on 2009-07-01
If you have root-access to the server, you can try running an ssh server there and transfer the to-be backuped files via ssh. Other means of transfer, such as rsync, maybe even ftp might be an option.

Probably a more simple workaround is to re-mount the share just before running the backup script, to make sure it is mounted properly, or at least try to determine whether the filesystem is still mounted prior to starting the backup script.

Good luck,
   Schilcha

---

### Post by bodhi.zazen on 2009-07-01
rsync would be a better back up solution.

---

### Post by ridshack on 2009-07-01
Thanks for the reply... Maybe Ill setup a cron to remount a few minutes before the backup job and email me if it fails.

---

