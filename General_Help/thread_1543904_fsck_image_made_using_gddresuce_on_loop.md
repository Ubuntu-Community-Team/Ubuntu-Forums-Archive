---
title: "fsck image made using gddresuce on loop"
date: 2010-08-01
forum: General Help
---

### Post by Lepy on 2010-08-01
I have a HDD that I was using as temporary storage (ext4) though I knew it was close to failing. Upon retrieval of the data, I found some of it was corrupted.

I unmounted and ran gddrescue on the whole device (/dev/sdd) using this command:
```
sudo ddrescue --no-split /dev/sdd /media/pool03/160image/image /media/pool03/160image/logfile
```

The image took ~24 hours to complete, and I can mount it using:
```
sudo mount -o loop,offset=32256 image.img /media/mount/
```

Of course, some of the files are still slightly corrupted, so I would like to fsck on the image to try and correct anything that can be. However, when trying this on the image, I get:
```
:/media/pool03/160image$ sudo fsck.ext4 -v -p  /media/pool03/160image/image.img 
fsck.ext4: Bad magic number in super-block while trying to open /media/pool03/160image/image.img
/media/pool03/160image/image.img: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

Here are some other interesting pieces of info:
```
:/media/pool03/160image$ sudo gpart ./image.img 

Begin scan...
End scan.

Checking partitions...
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

:/media/pool03/160image$ sudo mke2fs -n image.img
mke2fs 1.41.11 (14-Mar-2010)
image.img is not a block special device.
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
9773056 inodes, 39072726 blocks
1953636 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
1193 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872
```

gpart finds no useful info it seems, and trying to fsck using the -b option and the backups suggested by mke2fs results in the message above or (using a very high block):
```
:/media/pool03/160image$ dumpe2fs -o superblock=23887872 /media/pool03/160image/image.img 
dumpe2fs 1.41.11 (14-Mar-2010)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /media/pool03/160image/image.img
Couldn't find valid filesystem superblock.

```

As I said, the image can be mounted and the filesystem accessed. Many of the files seem ok and can be directly copied off of the mount, but I'd like see if some can be recovered or at the very least copy everything off the image, skipping the corrupted files (perhaps with a log of those skipped). 

None of the data is critical and will be ok if lost, but I'd still like to try recovering it just as a proof of concept. The original disk can still be used (very slowly), but I'd rather recover the data only using the image if possible.

Thanks!

---

### Post by dcstar on 2010-08-02
> **Lepy said:**
> 
.........
None of the data is critical and will be ok if lost, but I'd still like to try recovering it just as a proof of concept. The original disk can still be used (very slowly), but I'd rather recover the data only using the image if possible.


An "image" of a whole disk contains the partition table and then the partitions, you can only use fsck on the individual partitions, not the disk image as a whole.

You cannot recover data that is not there, fsck will only repair filesystem inode entries, it will not magically recover data lost due to bad blocks in the data areas.

---

### Post by Lepy on 2010-08-04
Good to know. I ended up using testdisk on the image. I then mounted it and all of the data copied without error. Everything seems uncorrupted, and I'm fairly certain everything is intact. 

I will have to try some sort of data carving tool on the image to see if any deleted data is recoverable, just for fun. The disk had ~8 gigs free while gddrescue listed ~1.5 gigs as errored.

Luckily, all is well. gddrescue is a great tool, but I hope I don't have to use it again. I'll make sure to put everything on my zfs array next time and back that up too!

---

