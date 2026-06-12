---
title: "udisk: &quot;only root can do that&quot;"
date: 2011-04-03
forum: General Help
---

### Post by bukzor on 2011-04-03
I'm trying to get automount for my cdrom to work properly.

When I put in a CD, the automount process fails with 

```

Unable to mount <name of DVD>!

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sr0 on /media/cdrom

```


I'm able to reproduce the problem at the command line:

```
$ udisks --mount /dev/sr0
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sr0 on /media/cdrom

```

but I'm stymied as to how to configure udisk, or even how to inspect what it's trying to do.

I've done a ton of googling, and all the answers I've come across either say "use sudo" or "install hal". These are workarounds, not solutions. The system should be able to auto-mount media without hal or sudo.

Thanks in advance,
--Buck

---

### Post by bukzor on 2011-04-03
I should add that my /etc/fstab is not the issue. "mount /media/cdrom" works perfectly, but udisk seems to be doing something more similar to this:

```
$ mount /dev/sr0 /media/cdrom
mount: only root can do that

```

--buck

---

