---
title: "resize2fs: Can't read next inode while trying to resize"
date: 2010-01-19
forum: General Help
---

### Post by bonfire89 on 2010-01-19
Hello there,

I'm currently in the process of remove a drive from an lvm.

I am following this guide

[http://ubuntuforums.org/showthread.php?t=449711](http://ubuntuforums.org/showthread.php?t=449711)

this is the 2nd drive that I am removing, the first one went off without a problem.

However, I just received this error


```
resize2fs: Can't read next inode while trying to resize /dev/vg0/lvol0
```

and I'm not sure what it means or where to go from here.

The entire output is

```
root@dude:/mnt# resize2fs -p /dev/vg0/lvol0 4466524456k
resize2fs 1.41.4 (27-Jan-2009)
Resizing the filesystem on /dev/vg0/lvol0 to 1116631114 (4k) blocks.
Begin pass 2 (max = 253665186)
Relocating blocks             XXXXXX----------------------------------
Begin pass 3 (max = 47104)
Scanning inode table          XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
resize2fs: Can't read next inode while trying to resize /dev/vg0/lvol0
```

what should I do at this point in order to complete the removal of the hard drive from the lvm?

Thank you.




additional info:

Just prior to this resize the df output is as so

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             19228276    949600  17301928   6% /
tmpfs                   642736         0    642736   0% /lib/init/rw
varrun                  642736        56    642680   1% /var/run
varlock                 642736         0    642736   0% /var/lock
udev                    642736       196    642540   1% /dev
tmpfs                   642736         0    642736   0% /dev/shm
lrm                     642736      2192    640544   1% /lib/modules/2.6.28-17-generic/volatile
/dev/sdd1            1442145212 1368627316    261096 100% /mnt/1.5
/dev/sdh1            1442145212 1367879596   1008816 100% /mnt/freed1
/dev/mapper/vg0-lvol0
                     6077137192 4382897544 1632522860  73% /mnt/lvm
```

---

### Post by bonfire89 on 2010-01-19
I'm currently running

```
e2fsck -f /dev/vg0/lvol0
```

to see what happens

---

### Post by bonfire89 on 2010-01-19
hmmmm

"Error reading block 1276051458 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>"

---

### Post by bonfire89 on 2010-01-30
I've borrowed some hard drives... off loading everything temporarily then putting it back on.


Problem abandoned.

---

