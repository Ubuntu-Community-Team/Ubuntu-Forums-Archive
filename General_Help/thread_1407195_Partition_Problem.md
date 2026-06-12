---
title: "Partition Problem"
date: 2010-02-15
forum: General Help
---

### Post by Neon612 on 2010-02-15
I had installed Ubuntu 9.04 on a Toshiba laptop I was planning on using for school. It has a 320GB HD, partitions for Toshiba junk, recovery disk junk, and Vista.

Originally, I made the Ubuntu partition 10GB, but now I want to enlarge it.

The Vista partition is down to around 80GB, the extended partition containing EXT3 and Swap is registering 210GB. But when I look at nautilus or my conky setup, the EXT3 part is only registering as 9.something GB, not the 200 some GB that I want it to be and that Gparted is showing.

What can I do to fix this?

---

### Post by jken146 on 2010-02-15
Please post the output of ```
sudo fdisk -l
```

---

### Post by Neon612 on 2010-02-15
fdisk:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x445c445b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         193       10390    81915435    7  HPFS/NTFS
/dev/sda3           37876       38914     8338432   17  Hidden HPFS/NTFS
/dev/sda4           10391       37875   220773262+   5  Extended
/dev/sda5           37814       37875      498015   82  Linux swap / Solaris
/dev/sda6           10391       37813   220275184+  83  Linux

Partition table entries are not in disk order

```

---

### Post by jken146 on 2010-02-15
Use a gparted on a Live CD to extend the partition you want to extend.

---

### Post by Neon612 on 2010-02-15
I did already. sda6 registers as 210GB in gParted but through nautilus or conky it only says 10GB.

---

### Post by jken146 on 2010-02-15
Oh. What does ```
df -h
``` say?

---

### Post by Neon612 on 2010-02-15
df -h:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.8G  6.5G  2.8G  70% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  140K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  168K  1.5G   1% /dev
tmpfs                 1.5G   76K  1.5G   1% /dev/shm
lrm                   1.5G  2.2M  1.5G   1% /lib/modules/2.6.28-16-generic/volatile

```

---

### Post by jken146 on 2010-02-15
Hmmm... looking at the output of fdisk, sda6 is indeed 210 GB.  Perhaps you resized the partition but not the filesystem. Did you use gparted to do this?

---

### Post by Neon612 on 2010-02-15
yes, I used gparted. I've always had great luck with it so far.

---

### Post by jken146 on 2010-02-15
You might need to take a more low level approach: [http://www.howtoforge.com/linux_resizing_ext3_partitions_p2](http://www.howtoforge.com/linux_resizing_ext3_partitions_p2)

---

### Post by Neon612 on 2010-02-16
> **jken146 said:**
> You might need to take a more low level approach: [http://www.howtoforge.com/linux_resizing_ext3_partitions_p2](http://www.howtoforge.com/linux_resizing_ext3_partitions_p2)

Thanks for the link. I tried it, ran on a Knoppix LiveCD. The fdisk section went through without a hitch. I rebooted, still in the LiveCD. And when I get to the part with the *e2fsck -f /dev/sda6* command I get something saying error in a super-block.

```
root@Microknoppix:/home/knoppix# e2fsck -f /dev/sda6
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda6

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

What does this mean? And what can I do to fix it? I'd like to get the full capacity back on my harddrive.

---

