---
title: "path to cdrom/DVD drive"
date: 2011-10-02
forum: General Help
---

### Post by SushiAddiction on 2011-10-02
Hi
I'm using Hyper's CDCatolog and to make my life a lot easier, I need a fixed path to the DVD drive.

At the moment I have to always select it manually under /media/DISKNAME

I've tried mount|grep ^'/dev'

/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
/dev/sdc1 on /media/FreeAgent type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0 on /media/A062 type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)

I've tried /dev/sr0 but it does not work.

Can anyone help? Thanks

---

### Post by mc4man on 2011-10-02
Don't know what Hyper's CDCatolog is so may not matter - (if anything to do with actual audio cd's

Anyway -  you can create a static mount dir. & add to fstab
Assuming the drive is /dev/sr0

```
sudo mkdir /media/cdrom0; gksudo gedit /etc/fstab
```

add this to a new line at bottom, save & restart
```
/dev/sr0 /media/cdrom0   udf,iso9660  user,noauto,exec,utf8   0    0
```

---

### Post by SushiAddiction on 2011-10-02
Thank you. It worked perfectly.

---

