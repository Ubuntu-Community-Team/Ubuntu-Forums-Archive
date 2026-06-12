---
title: "Mount hdd, which filesystem??"
date: 2009-07-05
forum: General Help
---

### Post by niiklas on 2009-07-05
Hello, im gonna mount a 1tb hdd to my server. Which file system should i pick?.

This is the way i would mount a hdd by google's help.

sudo mkdir /home/myusername/files
sudo mount /dev/sdb1 /home/myusername/files -t ntfs -o nls=utf8,umask=0222

---

### Post by HermanAB on 2009-07-05
XFS, JFS or Ext3.

XFS and JFS are very efficient.
Ext3 is the least efficient but it works.

---

### Post by niiklas on 2009-07-05
> **HermanAB said:**
> XFS, JFS or Ext3.

XFS and JFS are very efficient.
Ext3 is the least efficient but it works.

how should i write in terminal to format it to either xfs/jfs and mount it permanently?

---

