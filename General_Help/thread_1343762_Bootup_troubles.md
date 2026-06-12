---
title: "Bootup troubles"
date: 2009-12-02
forum: General Help
---

### Post by rasmus91 on 2009-12-02
Hi there.

My Class mates computer got wacked up. and won't boot giving the error message:

```
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try
```

And i'm at root prompt...

I've fiddled around on google a bit to find a solution. On different forums people are having this problem on ubuntu 9.10 (which this also is)

As much as i've read by now, i'd say the problems are related to the fstab file (/etc/fstab) i found a [link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468450"). which tells me to go there and "comment out" the line:

 # devpts /dev/pts devpts (rw,noexec,nosuid,gid=5,mode=620)

my problem is that the file looks like this:

```
#/etc/fstab: static file system information.
#
#use 'vol_id --uuid' to print the universally unique identifier for a
#device; this may be used with UUID= as a more robust way to name devices
#that works even is disks are added and removed. see fstab(5)
#
#<file system> <mount point> <type> <options> <dump> <pass>
proc            /proc         proc   defaults  0      0
# / was on /dev/sda1 during installation
UUID=b8d72eba-7a60-43b2-9df5-dfd8cd57042 /      ext4   relatime,errors=remount-ro 0    1
#swap was on /dev/sda5 during installation
UUID=34aa550-24ea-4036-a1dc-e60ae0f2ccfd none    swap  sw      0      0
```

The line isn't there.

Anyway, wether or not this is the problem, i would like some help.

Thanks in advance to anyone.

Cheers, Rasmus.

---

### Post by rasmus91 on 2009-12-03
Sorry, found out the HD was broken.

nevermind

---

