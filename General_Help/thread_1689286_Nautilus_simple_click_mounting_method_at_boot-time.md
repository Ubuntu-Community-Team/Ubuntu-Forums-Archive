---
title: "Nautilus simple click mounting method at boot-time"
date: 2011-02-16
forum: General Help
---

### Post by blackcoatman on 2011-02-16
Hello all,

I'm trying to find a way to auto-mount a couple of NTFS volumes at login (or even earlier if possible), **not** by editing fstab or running the (currently buggy for Maverick) ntfs-config tool, but by simulating the way that Nautilus mounts volumes when you click or double click on one. The reasons for this are not important (just to make things a little mysterious).

So, I checked the output of syslog when I click on an unmounted volume in Nautilus. It seems very useful, but I can't make much out of it. So I need your help :) I need to make something like a script to do this thing at startup.

```
Feb 16 20:52:28 UBUNTU-BCM-P5Q-DELUXE ntfs-3g[3701]: Version 2010.8.8 external FUSE 28
Feb 16 20:52:28 UBUNTU-BCM-P5Q-DELUXE ntfs-3g[3701]: Mounted /dev/sdb1 (Read-Write, label "Monster", NTFS 3.1)
Feb 16 20:52:28 UBUNTU-BCM-P5Q-DELUXE ntfs-3g[3701]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Feb 16 20:52:28 UBUNTU-BCM-P5Q-DELUXE ntfs-3g[3701]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096,default_permissions
Feb 16 20:52:28 UBUNTU-BCM-P5Q-DELUXE ntfs-3g[3701]: Global ownership and permissions enforced, configuration type 1
```

Any help and information is welcome. :)

---

### Post by wormyblackburny on 2011-02-16
when you double click it, it is using ntfs-config tool (technically) sinc it is the GUI front end for the ntfs-3g that you see in the lines above. The long and short of it is that i'm sure it would be possible to write a script and symlink it to rc.d so that it runs on boot, but why? /etc/fstab is the better way to go

and example of the command line for the shell script would be:

**mount -t ntfs-3g   /dev/sdb1   /path_to/mount_point**

---

### Post by blackcoatman on 2011-02-16
Unlikely, because ntfs-config is not even installed.
Also, to run a simple mount command one must be root.
I'm sure there is another way.

I have two ntfs volumes. The one mounts all-right by using fstab. The other one not. And even the one that mounts, I can't unmount it by simply clicking the eject button in nautilus, as I expect I could do If I mounted the volume the nautilus-way.

Also, see this more like an investigation. I'm really curious how it is possible to reproduce the nautilus way of mounting a volume with a script.

---

### Post by ParanoidSpiff on 2012-07-12
This seems to work 
udisks --mount /dev/sdXY

Mounts at the same place with the same permissions as nautilus.

---

