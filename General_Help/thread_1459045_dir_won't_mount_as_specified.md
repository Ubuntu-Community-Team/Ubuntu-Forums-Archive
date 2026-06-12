---
title: "dir won't mount as specified"
date: 2010-04-20
forum: General Help
---

### Post by bluethundr on 2010-04-20
Hello

 I've specified a directory on my new mail server that I would like to mount separately from the rest of the file system (along with a couple of others that do work correctly).

 I am specifying the directory as this in fstab:

```

/dev/sdm       /var/spool/mail/virtual ext3    defaults,noatime,noacl,data=ordered 1 2

```

But for some reason when the volume mounts it mounts as this:

```

root@cloud1:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.0G  753M  2.1G  27% /
varrun                854M   84K  854M   1% /var/run
varlock               854M  4.0K  854M   1% /var/lock
udev                  854M   48K  854M   1% /dev
devshm                854M     0  854M   0% /dev/shm
/dev/sda2             147G  188M  140G   1% /mnt
/dev/sdk              9.9G  129M  9.3G   2% /opt
/dev/sdl              9.9G  129M  9.3G   2% /var/www
/dev/sdm              493G  129M  468G   1% /var/mail/virtual

```

Why can't I mount this volume with the word "spool" as part of the file system name?

---

