---
title: "Hard Disc failure...?"
date: 2011-04-18
forum: General Help
---

### Post by tonewheelkev on 2011-04-18
Ubuntu 10.04 has just failed to load from my hard drive, so I've resorted to booting from CD just to get the machine going.
I'm wondering if my main boot drive has gone caput??

When trying to mount it using DISK UTILITY...get the message:

[B]_Error mounting volume_

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]

Is the drive stuffed....hoping you can help, I feel like I've had a leg cut off!!!

Kev  :confused:

---

### Post by TeoBigusGeekus on 2011-04-18
Open a terminal and give
```
sudo fsck /dev/sdb1
```
Try will scan the drive for errors and attempt to fix them.

---

### Post by tonewheelkev on 2011-04-18
Did  sudo fsck /dev/sdb1...and this is what came back

[PHP]ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sdb1: recovering journal
Error reading block 29932964 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Clearing orphaned inode 13765179 (uid=1000, gid=0, mode=0100644, size=32768)
Clearing orphaned inode 13762576 (uid=1000, gid=0, mode=0100600, size=48924)
Clearing orphaned inode 14811581 (uid=0, gid=0, mode=0100644, size=1750)
Clearing orphaned inode 14812292 (uid=1000, gid=0, mode=0100600, size=0)
Clearing orphaned inode 13894101 (uid=1000, gid=0, mode=0100644, size=1922112)
Clearing orphaned inode 13893671 (uid=1000, gid=0, mode=0100644, size=213920)
Clearing orphaned inode 14812291 (uid=1000, gid=0, mode=0100600, size=0)
Clearing orphaned inode 14812290 (uid=1000, gid=0, mode=0100600, size=0)
Clearing orphaned inode 14812284 (uid=1000, gid=0, mode=0100600, size=2048)
Clearing orphaned inode 14812282 (uid=1000, gid=0, mode=0100600, size=0)
Clearing orphaned inode 14812044 (uid=1000, gid=0, mode=0100600, size=512)
Clearing orphaned inode 14811981 (uid=1000, gid=0, mode=0100600, size=2048)
Clearing orphaned inode 14811754 (uid=1000, gid=0, mode=0100600, size=0)
Clearing orphaned inode 14811590 (uid=1000, gid=0, mode=0100600, size=512)
Clearing orphaned inode 12058750 (uid=0, gid=0, mode=040000, size=4096)
Clearing orphaned inode 13762658 (uid=1000, gid=0, mode=0100644, size=32768)
Clearing orphaned inode 13762609 (uid=1000, gid=0, mode=0100600, size=48724)
Clearing orphaned inode 13782978 (uid=1000, gid=0, mode=0100644, size=32768)
Clearing orphaned inode 13769516 (uid=1000, gid=0, mode=0100600, size=48092)
Clearing orphaned inode 13782914 (uid=1000, gid=0, mode=0100644, size=32768)
Clearing orphaned inode 13782908 (uid=1000, gid=0, mode=0100600, size=47252)
Clearing orphaned inode 13771227 (uid=1000, gid=0, mode=0100644, size=32768)
Clearing orphaned inode 13762768 (uid=1000, gid=0, mode=0100600, size=19128)
Clearing orphaned inode 13785644 (uid=1000, gid=1000, mode=0100644, size=32768)
Clearing orphaned inode 13762732 (uid=1000, gid=1000, mode=0100600, size=11892)
/dev/sdb1: clean, 450796/14950400 files, 50014384/59769600 blocks
ubuntu@ubuntu:~$[/PHP]

---

### Post by TeoBigusGeekus on 2011-04-18
It should be ok now. Try to get into Ubuntu and post back with the result.

---

### Post by tonewheelkev on 2011-04-18
> **TeoBigusGeekus said:**
> It should be ok now. Try to get into Ubuntu and post back with the result.

....Yippeeee...re-booted, and now working!!!

I LOVE this forum.....and many thanks **_TeoBigusGeekus_**:)

---

### Post by TeoBigusGeekus on 2011-04-18
Glad you've made it.
Don't forget to mark the thread as solved.

---

### Post by monkeyface766 on 2012-05-03
worked for me too! thanks!

---

