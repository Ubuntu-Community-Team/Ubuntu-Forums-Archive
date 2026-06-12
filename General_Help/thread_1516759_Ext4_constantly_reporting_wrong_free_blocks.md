---
title: "Ext4 constantly reporting wrong free blocks"
date: 2010-06-24
forum: General Help
---

### Post by AlexFox on 2010-06-24
Hi guys,

I'm using ubuntu 10.04 64bit server edition running a small dev server. What's happning though is that my one ext4 filesystems reports the wrong amount of free blocks. This is what fsck reports

```

fsck -n /dev/sda1 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Warning!  /dev/sda1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (6054663, counted=3855149).
Fix? no

Free inodes count wrong (8323288, counted=8323209).
Fix? no

/dev/sda1: ********** WARNING: Filesystem still has errors **********

/dev/sda1: 106280/8429568 files (0.2% non-contiguous), 27636473/33691136 blocks

```Now I restart and do a fsck which does sort out my problem, but the next day it's the same thing all over again. I've ended up forcing a fck and reboot every evening. Any idea what may be causing this?

---

### Post by Ichido on 2010-06-24
I had some troubles running Ubuntu 10.04 with ext4, so I went back to ext3.
I know this may not help you but have you tried ext3?

---

### Post by philinux on 2010-06-24
What happens if you use fsck -y.

---

### Post by Ichido on 2010-06-24
> **philinux said:**
> What happens if you use fsck -y.

Would you be so kind as to explain what this command does?
I'm guessing it's "File System Check" but what is "-y"?
Thanks in advance.

---

### Post by AlexFox on 2010-06-28
(From the man pages) fsck -y :

> For  some filesystem-specific checkers, the -y option will cause the fs-specific fsck to always attempt to fix any detected filesystem corruption automatically.  Sometimes an expert may be able to do better driving the fsck manually.


It will find and fix the free space issue, same as me forcing an fsck, but give it a day or two the free blocks issue shows up again. I've noticed it can something consume up to 10G of free space.

---

### Post by dcstar on 2010-06-28
> **AlexFox said:**
> Hi guys,

I'm using ubuntu 10.04 64bit server edition running a small dev server. What's happning though is that my one ext4 filesystems reports the wrong amount of free blocks. This is what fsck reports

```

fsck -n /dev/sda1 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
**Warning!  /dev/sda1 is mounted.**
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (6054663, counted=3855149).
Fix? no

Free inodes count wrong (8323288, counted=8323209).
Fix? no

/dev/sda1: ********** WARNING: Filesystem still has errors **********

/dev/sda1: 106280/8429568 files (0.2% non-contiguous), 27636473/33691136 blocks

```Now I restart and do a fsck which does sort out my problem, but the next day it's the same thing all over again. I've ended up forcing a fck and reboot every evening. Any idea what may be causing this?

**You** are causing this.

Never, ever do a fsck on mounted filesystems, data is not accurate because the filesystem is still in use.

Unmount the filesystem and then see what happens.

---

### Post by AlexFox on 2010-06-28
You may be right. I've done a full fsck with a live disc on the  unmounted partition, and get no such errors. However, df -h reports that  I'm using 121G of 127G Avail 0G

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             127G  121G   0G    0% /
none                   16G  180K   16G   1% /dev
none                   16G     0   16G   0% /dev/shm
none                   16G   64K   16G   1% /var/run
none                   16G     0   16G   0% /var/lock
none                   16G     0   16G   0% /lib/init/rw
tmpfs                  28G   28G  618M  98% /extents

```I may have been under the miss understanding that it was the "Free blocks / Inodes". Any idea what's happened to the other 6GB

---

