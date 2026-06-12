---
title: "Can't mount /home"
date: 2011-01-11
forum: General Help
---

### Post by darsu on 2011-01-11
My system has suddenly started halting with the following messages during startup:

```
init: ureadahead-other main process (...) terminated with status 4
init: ureadahead-other main process (...) terminated with status 4
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/home: waiting for UUID=de9d343a-711b-47d9-9589-87a92c39a6fd

```

Facts:
[LIST]
[*]In /etc/fstab the UUID of my /home partition entry matches the one above.
[*]Blkid lists all partitions except /dev/sda6 (=/home).
[*]/dev/sda6 does exist, and "fsck /dev/sda6" says it's clean.
[*]I can mount /home in the recovery shell without anything suspicious.
[/list]

Can anyone tell what's going on?

---

### Post by dcstar on 2011-01-12
> **darsu said:**
> 
.......
[LIST]
[*]In /etc/fstab the UUID of my /home partition entry matches the one above.
[*]**Blkid lists all partitions except /dev/sda6 (=/home)**.
[*]/dev/sda6 does exist, and "fsck /dev/sda6" says it's clean.
[*]I can mount /home in the recovery shell without anything suspicious.
[/list]

Can anyone tell what's going on?

Use **gparted** to see what the UUID of that partition actually is now.

---

### Post by darsu on 2011-01-19
Apparently there's something else to this–other people too have had disk UUID's disappear, eg.:

[http://ubuntuforums.org/showthread.php?t=1381617](http://ubuntuforums.org/showthread.php?t=1381617)

I somehow managed to recover /home by just mounting it by hand, but today /dev/sda2 was missing its UUID and my system bailed into Busybox. I fiddled randomly with menu.lst and chroot to no avail, then copied back the original menu.lst, and now it boots normally again for no apparent reason. I don't understand anything anymore, but I guess it's [solved] until next time.

---

### Post by muuu on 2011-09-19
I know this post is old, and im sorry but I feel I need to speak up.

If any of you are dual booting windows 7, then only enter the the win7 installer/recovery if you backed up all your partitions(Or if you are willing to lose any of them).

Ive had some of my partitions(ext2/3 and ntfs) disappear just from starting recovery once or booting from the win7 DVD.

I could recover them again using TestDisk.

---

