---
title: "Stupidly ran fsck while mounted and now won't boot!"
date: 2009-11-15
forum: General Help
---

### Post by sirsmilealot on 2009-11-15
Hello All,

For some silly reason at around 1AM I consented to running fsck while /dev/sda6 was still mounted - a lack of concentration has now led to serious problems!

I can no longer boot and suffer a number of messages, most notably these (cut from error messages):

```

Target filesystem doesn't have /sbin/init
ext_3 lookup: deleted inode referenced 369361
/bin/sh: can't open single
kernel panic - not syncing: Attempted to kill init!

```

I suspect data corruption has occured. I have tried booting from Live CD, mounted the partition as root and then attempted to reinstall ubuntu-minimal though I get:

```

Segmentation fault (core dumped)

```

..amongst warning messages. Surely there must be a way of using the intact version of aptitude on the Live CD and then instructing the install process to install ubuntu-minimal to the /dev/sda6 partition?

I sincerely hope someone can help me with this issue, especially since it has taken me so long to configure the system to work properly with my laptop. I'm also at University and this couldn't have come at a worse time!

Many thanks in advance - any help is appreciated.

Kindest Regards,

Paul.

---

### Post by mdurham on 2009-11-15
If you want to recover any of your data from that partition, **DO NOT** write anything to it. I don't know what Ubuntu-minimal is, but I bet if you try and install it, it will format the partition.

---

