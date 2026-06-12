---
title: "Disk full but really isn't?"
date: 2012-03-06
forum: General Help
---

### Post by mbspringer on 2012-03-06
create a two GB (2 GB)  image

dd if=/dev/zero of=/home/mbs/Desktop/fsfile bs=64k count=32768
dd if=/dev/zero of=fsfile bs=64k count=32768
mke2fs -m 0 -N 5000 fsfile
mount -o loop -t ext2 fsfile /home/mbs/Desktop/FSfile



The preceeding four commands create:
 
Type:     folder (inode/directory)
Contents: 1 item, with size 16.0 KB (some contents unreadable)
Location: /home/mbs/Desktop
Volume:   FSfile
Free space: unknown
           3.0 MB used
           2.0 GB free
Total capacity: 2.0 GB
Filesystem type: ext3/ext4
After installing some files, I get a properties listing:

Names: bin, dev, etc, lib, lost+found, mnt, proc
Type: folder (inode/directory)

Contents: 4,829 items, totaling 793.4 MB
Free space: 1.2 GB

***Despite this I cannot add any more files I get a disk full error***

Ubuntu 10.04

---

### Post by CharlesA on 2012-03-06
Moved to own thread.

---

### Post by matt_symes on 2012-03-06
Hi

> mke2fs -m 0 **-N 5000** fsfile

5000 inodes ? Any reason for this value ?

Try creating a filing system with more.

Kind regards

---

### Post by spiky001 on 2012-03-06
Hi

I have found when I shrink and resize a partition it has reported no space after. I then ran check file system with gparted it then regirsted the correct size

---

### Post by matt_symes on 2012-03-06
Hi

Just to clarify the number of inodes on my 10G partition.

```
matthew@matthew-Aspire-7540:~$ df -h | grep /dev/sda2
/dev/sda2       9.3G  8.0G  858M  91% /
matthew@matthew-Aspire-7540:~$ 
```

```
matthew@matthew-Aspire-7540:~$ sudo dumpe2fs /dev/sda2 | grep -i ^inode
dumpe2fs 1.42 (29-Nov-2011)
**Inode count:              610800**
Inodes per group:         8144
Inode blocks per group:   509
Inode size:               256
matthew@matthew-Aspire-7540:~$
```

I think this partition needs a clean out.

EDIT: Hello spiky001. I hope things are good for you.

Kind regards

---

