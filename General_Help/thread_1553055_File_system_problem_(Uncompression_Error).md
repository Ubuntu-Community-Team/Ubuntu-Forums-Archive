---
title: "File system problem? (Uncompression Error)"
date: 2010-08-14
forum: General Help
---

### Post by gloken on 2010-08-14
So I was playing StarCraft II in Wine, and the screen went black. I couldn't get into another shell, or get it to respond in any way, so I hit the reset button.

Grub tries to load my primary disk and it halts on an "uncompression error."

I promptly booted with a live disk, and mounted my drives. Everything mounts okay. 

Choking back panic, I begin backup.

Now I'm getting a read/write error on the files: 
cp: cannot stat user/dir/file.name: Input/output error


Can someone give me a quick assessment? Is this my file system dying? or my entire disk dying? 

What would a learned person do next? My best backup is still a few days old, so I'd rather not go to it if I can avoid it. Thanks!

---

### Post by gloken on 2010-08-14
I checked the drive with fsck -n and got the following output:

fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: No such file or directory while trying to open /dev/sd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by gloken on 2010-08-16
Looks like the disk had hardware issues. I've replaced it, shed my tears and moved on.

---

