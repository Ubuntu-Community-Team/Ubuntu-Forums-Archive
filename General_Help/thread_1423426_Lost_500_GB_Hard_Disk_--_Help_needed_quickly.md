---
title: "Lost 500 GB Hard Disk -- Help needed quickly"
date: 2010-03-06
forum: General Help
---

### Post by chmacka on 2010-03-06
I was watching a video with VLC and my computer freezed. After five minutes, I restarted it.

Now I can't mount my external 500 GB hard disk:

```
Unable to mount location

Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```**dmesg | tail**:

```
root@chmacka-desktop:~# dmesg | tail
[   15.348601] type=1505 audit(1267910059.838:22): operation="profile_replace" pid=1001 name=/usr/lib/cups/backend/cups-pdf
[   15.348971] type=1505 audit(1267910059.838:23): operation="profile_replace" pid=1001 name=/usr/sbin/cupsd
[   18.591171] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   18.591185] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   18.591260] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   24.704011] eth0: no IPv6 routers present
[   87.365555] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 2048 not in group (block 2236297792)!
[   87.366113] EXT3-fs: group descriptors corrupted!
[  337.155711] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 2048 not in group (block 2236297792)!
[  337.156338] EXT3-fs: group descriptors corrupted!

```**sudo fsck /dev/sdb1**

```
root@chmacka-desktop:~# sudo fsck /dev/sdb1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext3: Group descriptors look bad... trying backup blocks...
fsck.ext3: Bad magic number in super-block when using the backup blocks
fsck.ext3: going back to original superblock
fsck.ext3: Device or resource busy while trying to open /dev/sdb1
Filesystem mounted or opened exclusively by another program?
root@chmacka-desktop:~# 

```[SIZE=4]**I need help [COLOR=Red]urgently[/COLOR]!**[/SIZE]

---

### Post by patchwork on 2010-03-06
Run the fsck from a live cd, that way the drive isn't mounted.

---

### Post by chmacka on 2010-03-06
> **patchwork said:**
> Run the fsck from a live cd, that way the drive isn't mounted.
Tried that:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Group descriptors look bad... trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ 
```

EDIT: Forgot to mention - Hard Disk is divided in two partitions, one with NTFS filesystem, and another one with all of the important stuff with ext3 filesystem.

I can't open ext3 one, but I can open the NTFS partion without problems, both from live cd and normal boot.

---

### Post by mrprefect on 2010-05-07
Ran into a very similar problem so here is my solution:

I tried to run fsck from a live CD but it didn't make any difference and I know the system wasn't mounted anyway but you can run in from live CD if you want to be very sure nothing else is accessing the partition.

First you need to find where the superblock backups are kept on the disk, to do this you need to run mkfs.ext3 on the disk to see where it would store the backups.

mkfs.ext3 -n /dev/sdb1

make sure you put in the -n this makes it not actually write to the disk otherwise you are really up a creak

The superblock backup should be in the output, so now you can run fsck -b with one of the backup locations on the disk

fsck -b <superblock backup> /dev/sdb1

hope it works for you.

---

### Post by dino99 on 2010-05-07
sudo shutdown -F -r now

sudo dpkg --configure -a

---

### Post by P4man on 2010-05-07
Install testdisk from the repositories and let that figure it out.

---

### Post by micheledm on 2010-05-07
testdisk is lifesaver.

Give a look to this lifehacker post [http://lifehacker.com/5525534/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd](http://lifehacker.com/5525534/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd)

Good luck!

---

