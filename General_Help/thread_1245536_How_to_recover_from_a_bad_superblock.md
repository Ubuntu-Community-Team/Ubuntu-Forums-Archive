---
title: "How to recover from a bad superblock"
date: 2009-08-20
forum: General Help
---

### Post by conradin on 2009-08-20
Hi all,
I have a hard drive with a bad superblock. I have found tutorials to restore superblocks in solaris. Is there a good tutorial for restoring bad superblocks in Ubuntu? 

I do not want to format the drive, there was important data on this disk at one time.

---

### Post by P4man on 2009-08-21
something like this: ?
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

---

### Post by conradin on 2009-08-21
The article was a good start. But I still have some issues.

$ sudo e2fsck -f /dev/sdb1
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?

$ sudo dumpe2fs -f  /dev/sdb1 | grep -i superblock
dumpe2fs 1.41.4 (27-Jan-2009)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

$ sudo mke2fs -n /dev/sdb1
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
10010624 inodes, 40019915 blocks
2000995 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1222 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872


$ sudo e2fsck -f -b 32768 /dev/sdb1
e2fsck 1.41.4 (27-Jan-2009)
Superblock has an invalid journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Pass 1: Checking inodes, blocks, and sizes
Journal inode is not in use, but contains data.  Clear<y>? no

Error reading block 5668 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 8.  Ignore error<y>? yes

Force rewrite<y>? yes

Inode 8, i_blocks is 65616, should be 57424.  Fix<y>? yes

Error reading block 1343501 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error reading block 1343502 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? no

Error while scanning inodes (671744): Can't read next inode
Recreate journal<y>? yes

Creating journal (32768 blocks): Error : File exists 
	while trying to create journal
e2fsck: aborted



*************************
Eventually I gave up with the y [ENTER]
to continue thing. I bet there is a -y option 
Is recursively hitting "YES" a good idea?
Is there anything else I should try?

---

### Post by conradin on 2009-08-21
YES!!!!!!!!!!!!!!!!!!!!!!!!!
I got my data back!!!!!!!!!!

There is a recursive hit yes to continue option with the -y option
```

$ sudo e2fsck -f -b 32768 -y /dev/sdb1

```

THANK YOU P4man!!!!!

---

### Post by matiasw on 2010-01-24
**Edit**: nevermind, works again after a reboot.

I am experiencing the same problem. I have an LVM group with 2 physical disks. The logical volume is formatted as ext3. It worked fine, but when I rebooted, I suddenly got the errors described in this thread. But, for me 

> **conradin said:**
> ```

$ sudo e2fsck -f -b 1024 -y /dev/backup/nas

```

still outputs 
```

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/backup/nas
Could this be a zero-length partition?

```
after running the commands in conradin's posts (backup is the LVM group, nas is the formatted logical volume therein).

---

### Post by ZootHornRollo on 2010-05-15
> **P4man said:**
> something like this: ?
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

Thanks,

Worked for me.

---

### Post by mirajshah on 2010-07-21
[FONT=Garamond][SIZE=2]none of this worked for me, so I ended up formatting my filesystem with this guide: 
[http://www.cyberciti.biz/faq/howto-format-create-linux-filesystem/](http://www.cyberciti.biz/faq/howto-format-create-linux-filesystem/)

worked for me :D[/SIZE][/FONT]

---

### Post by conradin on 2013-04-02
Yah! im recovering my data again with this thread. (boo for power surges and corrupt super blocks.)

---

