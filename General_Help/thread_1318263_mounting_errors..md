---
title: "mounting errors."
date: 2009-11-07
forum: General Help
---

### Post by mitsuo on 2009-11-07
Hello, I've tried upgrading my kubuntu to 9.10 the other day, and during the post upgrade boot up, I got a strange message under the loading progress bar:

One or more of the mounts listed on /etc/fstab cannot yet be mounted:
/: waiting for /dev/disk/by-uuid/ab7f56f1-9680-40d5-a9df-bd77e72c57c9
/tmp: waiting for (null)
/boot: waiting for UUID=(some other uuid..)
/media/data: waiting for UUID=(some shorter uuid)
/windows: waiting for /dev/sda4
/media/data2: waiting for /dev/sdb1
swap: waiting for UUID=(...)
swap: waiting for /dev/sda5
Press ESC to enter a recovery shell

So I hit ESC...

# promt pops up..

I try :
# umount -a & mount -a
umount: /proc/sys/fs/binfmt_misc: not mounted
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
mount: /dev/sda1 already mounted or /boot busy
fuse: failed to create temporary directory.
fuse: failed to create temporary directory.
fuse: failed to create temporary directory.
[1]+  Exit 1                 umount -a

How do I proceed?

Thanks in advance..

---

