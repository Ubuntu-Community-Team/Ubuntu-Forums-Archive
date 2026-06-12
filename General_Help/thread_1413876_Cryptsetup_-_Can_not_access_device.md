---
title: "Cryptsetup - Can not access device"
date: 2010-02-23
forum: General Help
---

### Post by HDave on 2010-02-23
Hi -- total 100% panic here!

I have 10 hotswappable SATA drives I use for a rotating backup system.  On each drive I have created an encrypted LUKS partition.  I normally mount the drive by first unlocking it via:

```
cryptsetup luksOpen /dev/sdc1: BD-4-B
```

However some time last week this command refused to work...for any of the drive.  Before I even get prompted for a password I get the terse error message:  "Command failed: Can not access device"

I can't recall if it was a system update that broke it, but now I can't get to any of the data on these devices nor can I run any backups.  HELP!

---

### Post by HDave on 2010-02-23
Think I found the right bug:

[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/433051](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/433051)

---

