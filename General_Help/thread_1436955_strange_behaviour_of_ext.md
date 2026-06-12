---
title: "strange behaviour of ext"
date: 2010-03-23
forum: General Help
---

### Post by MelDJ on 2010-03-23
when i format my pendrive to any ext format (ext2-ex4), i have to be root to move anything into it. and i also have 6.8gb after i format it (its an 8gb pendrive). and moving 4gb of stuff takes 2 hours

when i format it to fat32, i can move things as a normal user and it has 7.3gb after i format it. 

anyone can clarify whats going on?

---

### Post by Seq on 2010-03-23
It may be easier to just stick with a simple filesystem on your removable drive.

> **MelDJ said:**
> when i format my pendrive to any ext format (ext2-ex4), i have to be root to move anything into it.
(..snip..)
when i format it to fat32, i can move things as a normal user

ext filesystems use permissions. You can change the owner of the filesystem from a terminal. Where "username" is your username, and "my-usb-key" is the name your usb key is mounted as.

```
$ sudo chown username /media/my-usb-key
```

This will persist across machines, but ownership is based on numeric ID, so you may not have easy access on other machines.

> **MelDJ said:**
> 6.8gb after i format it (its an 8gb pendrive). 
(..snip..)
when i format it to fat32, (...) it has 7.3gb after i format it. 

ext filesystems typically reserve 5% of the disk for root access. This is a safety feature. If some user were to fill the disk, 5% is remaining for a root user to log in to fix everything. Sysloggers keep working, etc.

If you want to disable this, you will want to unmount (but *not* eject) your usb drive. Where my-usb-key is again the name of your key, and /dev/sdXX is the device. This can be determined via the first mount/grep combination.

```
$ mount | grep my-usb-key
$ sudo umount /media/my-usb-key
$ sudo tune2fs -m 0 /dev/sdXX
```

> **MelDJ said:**
> and moving 4gb of stuff takes 2 hours

Can't help here. No idea how fast this things should be going.

---

### Post by MelDJ on 2010-03-23
thanks.
a few questions though
1. whats a simple filesystem? 
2. i always used ext for my pendrives and never had such ownership problems. only when i format in karmic this happened. is this a karmic feature?
3. it used to take about a few minutes. (jfs even faster)

---

### Post by Seq on 2010-03-23
> **MelDJ said:**
> thanks.
a few questions though
1. whats a simple filesystem? 
2. i always used ext for my pendrives and never had such ownership problems. only when i format in karmic this happened. is this a karmic feature?
3. it used to take about a few minutes. (jfs even faster)

1. Simple would be something without permissions (or very many features). Such as fat32
2. Odd. Permissions have always taken effect for me. As far as I know, you can't bypass them on ext filesystems.
3. Don't know what to tell you.

---

