---
title: "fsck.jfs won't work after crash"
date: 2009-10-12
forum: General Help
---

### Post by Weidbrewer on 2009-10-12
I have a RAID set up on my server.  There was a power failure that caused this machine to go off line, and when I rebooted, the RAID did not mount.  No biggie, this has happened before.  In the past, I have done this:

```
sudo fsck.jfs -a /dev/md1

```

And then:

```
sudo mount /media/raid

```

However, when I just tried this, I got:

```
*****@****:~$ sudo fsck.jfs -a /dev/md1
sudo: fsck.jfs: command not found

```

That's never happened before.  OS is Ubuntu 64 8.10, and the two halves of the RAID are mounted as /dev/sda and sdb.  (Gparted then shows them as sda1 and sdb1 in the main screen.)  Help would be greatly appreciated, as I really need this system back up and running tonight, if possible.

---

### Post by Weidbrewer on 2009-10-12
Huh.  Very weird.  I found the issue.  jfsutils was not installed...this is strange because I've used it on here before, and I certainly didn't do anything that should have uninstalled it.  For anyone else that has the problem:

```
sudo apt-get install jfsutils

```

Then run my commands above.  File system mounts as normal.

---

