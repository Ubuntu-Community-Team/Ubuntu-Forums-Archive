---
title: "Trouble Mounting root.disk on Ubuntu 12.04 Alpha"
date: 2012-02-27
forum: General Help
---

### Post by Amanitas on 2012-02-27
From the title, I am using Ubuntu 12.04 alpha which could be the root of my problem. I had wubi installed back in the day and so I saved the root.disk files that puts on the harddisk. I am now trying to access those root.disk files to retreive files from it.

when I ran
```
sudo mount -o loop root.disk /mnt
```it spits out
```
mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```From what I have found, it seems like it thinks the filesystem is ext2 but apparently not. The root.disk file that I am using is from a 11.10 installation it that helps.

What am I doing wrong?

---

### Post by bcbc on 2012-02-27
Have you tried to fsck it?

---

