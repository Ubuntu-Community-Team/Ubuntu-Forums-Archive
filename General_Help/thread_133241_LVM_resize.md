---
title: "LVM resize"
date: 2006-02-19
forum: General Help
---

### Post by evilgold on 2006-02-19
Hi,

I need to split my current / partion into two seperat ones (/ and /home) I'm using ext3 on a LVM volume over 2 hard disks. How would i go about doing this without destroying everything.

---

### Post by RAOF on 2006-02-19
The appropriate man pages are for: resize2fs, lvresize, lvcreate.

As I see it (warning: **I haven't done this before**.  This is just from reading the man pages) you need to:
1) Resize your / **filesystem** with resize2fs.
2) Resize your / **logical volume** (aka: partition) with lvresize
3) Create a new logical volume with lvcreate
4) Format the new lv with mkfs.ext3
5) Add a mount point for your new drive (as /home, or whatever) in fstab

You shouldn't need to worry about anything lower-level than the logical-volume.  Specifically, the fact that your volume-groups span multiple drives shouldn't matter.

---

### Post by evilgold on 2006-02-19
Thank you for the reply.

just one more question. In order to do what you suggested i need to unmount /... how do i do that. I've tried starting up using 'single' but no matter how many times it type umount /, it does nothing.

---

### Post by RAOF on 2006-02-19
[QUOTE=evilgold]Thank you for the reply.

just one more question. In order to do what you suggested i need to unmount /... how do i do that. I've tried starting up using 'single' but no matter how many times it type umount /, it does nothing.[/QUOTE]
Oh, whooops!  Sorry, of course you'll need to unmount /.

In order to do that, you'll need to boot from a livecd.  As far as I know, there's no way to unmount the root drive that you've booted from.

The Ubuntu live cd should have all the tools you need to do this on it.  Knoppix & the System Rescue CD probably also have the needed tools, but I'm not sure.

---

