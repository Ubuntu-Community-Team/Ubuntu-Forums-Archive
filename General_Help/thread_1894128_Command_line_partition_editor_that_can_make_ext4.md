---
title: "Command line partition editor that can make ext4"
date: 2011-12-11
forum: General Help
---

### Post by Cool Javelin on 2011-12-11
Does someone know of a partition editor for 10.10 that can make an ext4 partition.

It seems parted can only make an ext3 partition.

I have no graphics desktop, only a server.

Thanks, Mark.

---

### Post by lswb on 2011-12-11
> **Cool Javelin said:**
> Does someone know of a partition editor for 10.10 that can make an ext4 partition.

It seems parted can only make an ext3 partition.

I have no graphics desktop, only a server.

Thanks, Mark.
 Take a look at the man page for mkfs.ext4 or mke2fs.

---

### Post by Cool Javelin on 2011-12-11
Great, lswb, thanks.

Mark.

---

### Post by Cool Javelin on 2011-12-12
I am having some difficulties with mkfs.ext4.

I used parted to remove the ntfs partition from /dev/sdd

Then, entering the command (note the 1 after sdd,) it complains

```
mark@aserver:/etc$sudo mkfs.ext4 /dev/sdd1
mke2fs 1.41.11 (14-Mar-2010)
Could not stat /dev/sdd1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
```

if, on the other hand, I do the following, (no 1 after sdd) (I accented a key message it complains about)

```
mark@aserver:/etc$sudo mkfs.ext4 /dev/sdd
mke2fs 1.41.11 (14-Mar-2010)
[I]/dev/sdd is entire device, not just one partition!
Proceed anyway? (y,n)[/I] y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
4890624 inodes, 19537686 blocks
976884 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
597 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 21 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
```

This apears to work, but sdd does not show up on blkid

```
mark@aserver:/etc$blkid
/dev/sda1: UUID="771c95be-6b96-471a-97b6-812e81778419" TYPE="ext4"
/dev/sda2: UUID="e4cae75b-2247-4b89-8178-1475b702d0b7" TYPE="swap"
/dev/sdb1: UUID="d5b00ac0-f1e8-41db-b65e-8a3834b27c3d" TYPE="ext4"
/dev/sdc1: UUID="daf1c1c1-5d58-4f41-9a6e-bf3b38da1a18" TYPE="ext4"
```

I am able to mount it

```
mark@aserver:/etc$sudo mount /dev/sdd /80G
```

and it appears to work

```
mark@aserver:/etc$cd /80G
mark@aserver:/80G$ ll
total 24
drwxr-xr-x  3 root root  4096 2011-12-11 23:49 ./
drwxr-xr-x 24 root root  4096 2011-12-11 17:58 ../
drwx------  2 root root 16384 2011-12-11 23:49 lost+found/

```

and

```
mark@aserver:/80G$df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             13716828    566704  12453344   5% /
none                    120296       196    120100   1% /dev
none                    124500         0    124500   0% /dev/shm
none                    124500       576    123924   1% /var/run
none                    124500         0    124500   0% /var/lock
none                    124500         0    124500   0% /lib/init/rw
/dev/sdb1             26333052    909184  24086220   4% /usr
/dev/sdc1             38473364   1002488  35516524   3% /40G
/dev/sdd              76923000    184084  72831380   1% /80G
```

but I don't know if it is right, or stable, and of course, I would like to mount it using UUID that I can't seem to get.

Any Ideas?

Thanks, Mark.

---

### Post by Elfy on 2011-12-12
Should be able to use tune2fs to create an UUID for it - some information here [http://ubuntuforums.org/showthread.php?t=1378527](http://ubuntuforums.org/showthread.php?t=1378527)

---

### Post by lswb on 2011-12-12
Try using the command "sudo blkid -c /dev/null" For reasons I don't understand, the blkid command caches it's results in a file somewhere and reports that rather than actually checking the system each time. the " -c /dev/null" option tells blkid to use /dev/null as its cache file and since its empty, it then rereads the system.

Also I think you still need to create the partition with parted, and then use mke2fs to actually build the filesystem on that partition (or to "write over" an older filesystem already present on an existing partition) I believe that is why you see the error message about using the entire device.

---

### Post by The Cog on 2011-12-12
It is not normal to write a filesystem to the raw disk (sdd). It is normal practice to create a partition table on sdd and then create partitions sdd1, sdd2 etc.

You can use fidsk or parted to create a partition table on sdd. Then add a partition (sdd1) and set the type to 83 (the Linux partition type). Once you have created the partition, you can format it with mkfs.ext4.

You may find it easier to use the graphical gparted from a live CD.

---

### Post by Cool Javelin on 2011-12-14
Thanks forestpiskie, lswb, and The Cog.

All is well now, thanks for all your help.
---
lswb, I did read about blkio, and found found all the non intuitive stuff, and was able to get it to report properly.

Turns out the sdd drive really was there, and it did show a UUID.

Still had the issue of it being reported as sdd rather then sdd1.

Used Parted and made the partition only, then tried to use the command line mkfs.ext4 to make the file system, but I guess I was still not understanding it.

I finally did as The Cog suggested and used the live CD and Gparted.

I hesitated to do that because last time, the system wouldn't boot after. But I think that was because the fstab file was wrong and Ubuntu wouldn't get past it.

In retrospect, I should have commented out the line in fstab that referred to the sdd disk.

Thanks for all your's help,
Mark.

---

