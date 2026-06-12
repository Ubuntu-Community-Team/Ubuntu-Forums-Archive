---
title: "Help resizing LUKS partition"
date: 2011-11-10
forum: General Help
---

### Post by renegadeandy on 2011-11-10
Following the following guide:

[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

I am at line sudo e2fsck -f /dev/mapper/crypt1 and this is the output:

```

umount: /dev/mapper/crypt1 is not mounted (according to mtab)
ubuntu@ubuntu:~$ sudo e2fsck -f /dev/mapper/crypt1
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Device or resource busy while trying to open /dev/mapper/crypt1
Filesystem mounted or opened exclusively by another program?

```

I presume /dev/mapper/crypt1 is correct - i think it says crypt 1 because I did :

```

sudo cryptsetup luksOpen /dev/sda2 crypt1

```

Can somebody help me? I am doing all of this - and typing this from a livecd!

---

