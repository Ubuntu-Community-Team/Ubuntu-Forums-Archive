---
title: "mounting virtual disks on loop without root privilege"
date: 2010-12-19
forum: General Help
---

### Post by rkpisanu on 2010-12-19
Is it possible to mount virtual disks on loop without root privilege ?
Here the sudo version to avoid:

```

dd if=/dev/zero of=new.root.bin bs=1024k count=150
mkfs.ext3 ./new.root.bin
mkdir /tmp/smaller
sudo mount -o loop new.root.bin /tmp/smaller

```Thanks.

---

