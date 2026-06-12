---
title: "External HD won't wipe"
date: 2009-12-11
forum: General Help
---

### Post by edwin_cheung88 on 2009-12-11
Hey all!

A really weird request...

I have on hand a really old 250 GB lacie External HD.

I mounted it and edited it fine on my mac, but a slight burp and it only recognized on my Ubuntu.

=( Sad to say, I'm more than happy to reformat this sucker and start over... thing is... I can't

Gparted gets errors, 

fsck gets

> 
eddie@eddie-desktop:~$ sudo fsck -r /dev/sdb1
fsck from util-linux-ng 2.16
fsck: fsck.hfsplus: not found
fsck: Error 2 while executing fsck.hfsplus for /dev/sdb1

and mount gets

> eddie@eddie-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eddie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eddie)
/dev/sdb1 on /media/External HD type hfsplus (rw,nosuid,nodev,uhelper=devkit)

=) Any help would be appreciated!

I'm willing to blow anything up, I've already deleted my ubuntu (twice!) with fsck and gparted by accident! So I'm in a pretty epic battle with this lacie (it's winning =( )

---

### Post by Leppie on 2009-12-11
You might want to have a look at [this page]("http://ubuntuforums.org/showthread.php?t=392287").

---

### Post by Leppie on 2009-12-11
Actually, I think you need to install hfsplus on your system:
```
$sudo apt-get install hfsplus hfsutils hfsprogs
```

then try to run fsck again.

---

### Post by edwin_cheung88 on 2009-12-11
Got some apt-get installs, ran fsck again...

> fsck from util-linux-ng 2.16
** /dev/sdb1
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Rebuilding Catalog B-tree.
** Rechecking volume.
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Checking Catalog hierarchy.
   Invalid directory item count
   (It should be 5 instead of 2)
** Checking Extended Attributes file.
** Checking volume bitmap.
   Volume Bit Map needs minor repair
** Checking volume information.
** Repairing volume.
** Rechecking volume.
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Checking Catalog hierarchy.
** Checking Extended Attributes file.
** Checking volume bitmap.
** Checking volume information.
** The volume External HD was repaired successfully.


It says it repairsed successfully, but when i go plug it in back into my MacBook, the Mac still doesn't recognize it. =(

Is there any way to wipe a HFS+ from the ubuntu?

---

### Post by Leppie on 2009-12-12
Just use fdisk, cfdisk, gparted or whatever partition manager you prefer.

Try to mount it in Ubuntu first, see what you want to keep. Then format it with gparted (remember that in gparted you actually need to click the big check sign in order to execute the indicated operations).

---

### Post by edwin_cheung88 on 2009-12-12
Nope =( Gparted gives me this log file...

---

