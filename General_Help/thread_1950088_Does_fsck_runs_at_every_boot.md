---
title: "Does fsck runs at every boot?"
date: 2012-03-31
forum: General Help
---

### Post by Eugene_ on 2012-03-31
Hi.

Installed Xubuntu 11.10 and every time I boot there's messages in var/log/boot.log:

fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
/dev/sda3: clean, 187887/3842048 files, 1338512/15360000 blocks
/dev/sda7: clean, 1493/16007168 files, 3881725/64000000 blocks
/dev/sda6: clean, 21691/12804096 files, 2875117/51200000 blocks

Does it mean that fsck runs at every startup? Or it simply loads looks for some flag and don't check anything?


When I force it with /forcefsck it shows something like this:
fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
/dev/sda3: 187892/3842048 files (0.2% non-contiguous), 1334830/15360000 blocks
/dev/sda7: 1494/16007168 files (1.5% non-contiguous), 4227863/64000000 blocks
/dev/sda6: 21607/12804096 files (0.7% non-contiguous), 2874437/51200000 blocks


Thanks for assistance!

---

### Post by codemaniac on 2012-03-31
Unless you tweak the settings, a full fsck is run every 30 or 27 boots as i remember .fsck runs on every boot by default, but it doesn't actually run a file system check unless you are at the mount/time limit or unless you tell it to run a check like /forcefsck .

---

### Post by codemaniac on 2012-03-31
You can also find the community documentation on fsck useful .
[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

### Post by raja.genupula on 2012-03-31
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by Eugene_ on 2012-03-31
Thanks!

Just wanted to be sure that it not performs check at every startup.
And it seems to be good idea with AutoFsck.

---

### Post by dcstar on 2012-03-31
> **codemaniac said:**
> Unless you tweak the settings, a full fsck is run every 30 or 27 boots as i remember .fsck runs on every boot by default, but it doesn't actually run a file system check unless you are at the mount/time limit or unless you tell it to run a check like /forcefsck .

EXTn filesystems have a default setting to run fsck after *n mounts* or *n period* that can be changed by the **tune2fs** tool:

```
man tune2fs
```

If a filesystem was not unmounted correctly before a shutdown then it is considered "dirty" and fsck should run on it automatically on the next boot.

If this happens on every boot then you have an issue with filesystems not being unmounted correctly.

---

### Post by codemaniac on 2012-04-01
> **dcstar said:**
> EXTn filesystems have a default setting to run fsck after *n mounts* or *n period* that can be changed by the **tune2fs** tool:

```
man tune2fs
```

If a filesystem was not unmounted correctly before a shutdown then it is considered "dirty" and fsck should run on it automatically on the next boot.

If this happens on every boot then you have an issue with filesystems not being unmounted correctly.

Thanks dcstar , for the valuable information .

---

### Post by Eugene_ on 2012-04-01
Thanks for all the replies!

It seems in "sudo dumpe2fs -h /dev/sda3" output there's field called "Last checked" which tells when was last time filesystem was checked (in my case it was when I forced check with /forcefsck).

So it seems that these lines in /var/log/boot.log not necessarily mean that fsck performed check, only that it loaded into memory:

fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
/dev/sda3: clean, 187887/3842048 files, 1338512/15360000 blocks
/dev/sda7: clean, 1493/16007168 files, 3881725/64000000 blocks
/dev/sda6: clean, 21691/12804096 files, 2875117/51200000 blocks

---

