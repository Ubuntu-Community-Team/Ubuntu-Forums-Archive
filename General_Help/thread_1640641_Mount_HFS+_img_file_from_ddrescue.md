---
title: "Mount HFS+ img file from ddrescue"
date: 2010-12-08
forum: General Help
---

### Post by isahlos on 2010-12-08
Hi,

I'm trying to mount a .img file with a HFS+ partiton on it. I can't seem to get it working. I don't want to overwrite a whole partition. Just mount the filesystem to /media/directory.

sudo mount -t hfs -o loop /path/file.img /media/directory/ gives me wrong fs type, bad option, bad superblock on /dev/loop0,


Output: dmesg | tail
[665583.878826] hfs: unable to find HFS+ superblock
[690232.956830] hfs: can't find a HFS filesystem on dev loop0.

Anyone has experience in this? Thanks!

---

### Post by acmeinc on 2011-04-29
I'd like to re-open this thread.  I'm having the same problem when attempting to loop mount a ddrescue'd OSX disk using Ubuntu 10.04.

---

### Post by metallus on 2011-09-22
Hello, I am having the same problem with a hfs img. Any news?

---

### Post by dcstar on 2011-09-22
> **isahlos said:**
> Hi,

**I'm trying to mount a .img file with a HFS+ partiton on it**. I can't seem to get it working. I don't want to overwrite a whole partition. Just mount the filesystem to /media/directory.

sudo mount -t hfs -o loop /path/file.img /media/directory/ gives me wrong fs type, bad option, bad superblock on /dev/loop0,


Output: dmesg | tail
[665583.878826] hfs: unable to find HFS+ superblock
[690232.956830] hfs: can't find a HFS filesystem on dev loop0.

Anyone has experience in this? Thanks!

It is illogical to try and mount a whole disk when you are trying to mount a partition within the disk image:

[http://wiki.edseek.com/guide:mount_loopback](http://wiki.edseek.com/guide:mount_loopback)

---

