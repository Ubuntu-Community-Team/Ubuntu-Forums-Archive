---
title: "fsck on 4TB raw image file: memory allocation failed"
date: 2011-12-12
forum: General Help
---

### Post by Die Mensch-Maschine on 2011-12-12
Hi,

I’ve got a dying 4TB RAID volume. To recover the data which couldn’t be salvaged, I’ve duplicated the whole volume with GNU ddrescue (a few MB are still missing). I’d like to run fsck on the partition contained in this image, but when I do on 10.04.3 LTS, fsck fails with a memory allocation issue.

Do anyone have an idea why this happens, how to circumvent the issue, or how to apply fsck on an image file some other way? Thanks.

**More details**

Here is how I proceed to apply a fsck on the image file **raid.img**:

```
$sudo gdisk -l raid.img
# cut ...
Number  Start (sector)    End (sector)  Size       Code  Name
   1              34      7809773534   3.6 TiB     0700  
```
The (single) partition which contains the data is at sector 34, which means an offset of 43 sectors * 512 bytes/sector = 17408 bytes. The **tee** is just for logging purposes.
```
$sudo losetup -o 17408 /dev/loop0 raid.img
$sudo fsck -v -y /dev/loop0 2>&1 | tee --append fsck.log
```

fsck runs for a while, then ends on:
```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/loop0 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 4038521 has illegal block(s).  Clear? yes

Illegal double indirect block (1095762021) in inode 4038521.  CLEARED.
Illegal double indirect block (1095761967) in inode 4038521.  CLEARED.
Inode 4038521 is too big.  Truncate? yes

Block #838861840 (226908799) causes directory to be too big.  CLEARED.
Error storing directory block information (inode=4038521, block=0, num=672418440): Memory allocation failed
e2fsck: aborted
```

Various posts found through Google indicates that a common solution to this issue are:
[list=1][*]To run a 64-bit fsck on a 64-bit system. This should the case.
[*]To append
```
[scratch_files]
directory = /some/directory/
``` to /etc/e2fsck.conf. I did it, just in case. Stuff does get written in the directory, but the error remains the same.[/list]

**Configuration**

Ubuntu version 10.04.3 LTS x86_64.
```
$ uname -srvmo
Linux 2.6.32-33-server #72-Ubuntu SMP Fri Jul 29 21:21:55 UTC 2011 x86_64 GNU/Linux
$file $(which e2fsck)
/sbin/e2fsck: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
```

---

