---
title: "Move /usr to zfs-fuse"
date: 2010-08-24
forum: General Help
---

### Post by singpolyma on 2010-08-24
I thought the system was supposed to get through the early stages of booting without /usr so I moved it to a filesystem on my zfs-fuse pool, and created a symlink from /usr to /media/zfs/usr

On reboot it would not boot.  Hitting esc to see the messages showed network-manager, avahi-daemon, and squid all failing to start (the first two before the ZFS mount success message came up, the other one after).  The system was doing nothing.

Somehow, however, the system was still able to boot into the root shell of recovery mode, which I used to out /usr back on the main ext4 partition and now it's booting fine.

Should this be something I'm able to do?  Are there specific parts of /usr I need to leave?  Should I try to figure out how to make ZFS mounts happen even sooner than whatever the zfs-fuse package defaults to?

---

### Post by srs5694 on 2010-08-24
In Linux, ZFS is only supported by the Filesystems in Userspace (FUSE) package, which is a userspace filesystem interface, meaning it's kept at "arm's length" from the kernel code. This approach degrades performance but makes it easier to write a filesystem. In the case of ZFS, the ZFS license is incompatible with the GPL that the Linux kernel uses, so unless the ZFS license terms change, ZFS is never likely to become an official part of the Linux kernel.

Using a userspace filesystem for a critical partition such as /usr is a Bad Idea; /usr should be on a Linux-native kernel-space filesystem. In theory, what you tried might work, but there are plenty of reasons it might not -- FUSE might rely on files stored in /usr, the system might become unreliable if you got it to mount, etc. I don't know what specific problem caused the attempt to fail completely, but my guess is that FUSE (or its ZFS module) relies on files in /usr. I couldn't find a specific file that might cause this problem on Ubuntu, but on my Gentoo system, some FUSE libraries are definitely stored in /usr. It's entirely plausible that there's some obscure but necessary ZFS file on /usr even on an Ubuntu system, and I just missed it.

If you need ZFS-style features on /usr, I recommend you look instead at Btrfs. This is Linux's next-generation filesystem, with many ZFS-like features. Btrfs was still considered experimental the last I checked, but it's implemented by a kernel-space driver (vs. the userspace driver for ZFS), and it's a Linux-native filesystem. I wouldn't recommend this for a real production system, though, since Btrfs is still experimental. On a production system, stick with one of the stable Linux filesystems -- ext2fs, ext3fs, ext4fs, ReiserFS, JFS, or XFS. Of those, ext2fs lacks a journal and so isn't a good choice, but any of the others should be acceptable for /usr.

---

### Post by singpolyma on 2010-08-24
> **srs5694 said:**
> In Linux, ZFS is only supported by the Filesystems in Userspace (FUSE) package, which is a userspace filesystem interface, meaning it's kept at "arm's length" from the kernel code. This approach degrades performance but makes it easier to write a filesystem. In the case of ZFS, the ZFS license is incompatible with the GPL that the Linux kernel uses, so unless the ZFS license terms change, ZFS is never likely to become an official part of the Linux kernel.

Right, I'm quite aware of the problem with the existing ZFS code base :)  Hence why I'm using ZFS-fuse.

> **srs5694 said:**
> Using a userspace filesystem for a critical partition such as /usr is a Bad Idea; /usr should be on a Linux-native kernel-space filesystem.

Are there good reasons it's a bad idea?  I've been using ZFS for my homedir for months with only one (well-known) issue.

Someone on twitter suggested that the problem is likely that I'm using a symlink.  If there's a really good reason not to use ZFS for /usr, though, I don't have to.  The biggest reason I want it is to create snapshots every time I use apt so that I can get rollback.

> **srs5694 said:**
> If you need ZFS-style features on /usr, I recommend you look instead at Btrfs.

Right, I know btrfs.  It's less stable/well tested than ZFS, though, and probably always will be.  Most NiH projects have that problem.  Of course, I'm biased, since I really *really* wish that someone would create a second implementation of ZFS.  Multiple open interoperable implemenations of anything other than FAT/NTFS would be very awesome, esp if it were ZFS, then we could make ZFS a standard in the filesystem world :)

---

