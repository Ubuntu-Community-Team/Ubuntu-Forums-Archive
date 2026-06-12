---
title: "Multiple problems with HFSPlus"
date: 2010-02-11
forum: General Help
---

### Post by blueyelabs on 2010-02-11
Hi all,

I have a SheevaPlug which I use as a home file-server and effective "TimeCapsule" for when I'm abroad. The SheevaPlug is permanently on, obviously, but we recently had a power cut (it was short but it obviously cut the power to the plug). I then had to boot it via a physical console to make sure it was working. Everything loaded fine and my external hard-drive was mounted as HFSPlus but as read-only. I would like to stress that before this everything was working fine, it was mounted as read/write hfsplus. I tried remounting but to no avail.
I then tried to run "fsck.hfsplus" on both partitions and the output was as follows:

```

user@plug:~$ sudo fsck.hfsplus /dev/sda1
** /dev/sda1
** Checking HFS Plus volume.
** Checking Extents Overflow file.
   Invalid index link
(3, 230)
** Repairing volume.
** Rechecking volume.
** Checking HFS Plus volume.
** Checking Extents Overflow file.
   Invalid index link
(3, 230)
** Repairing volume.
** Rechecking volume.
** Checking HFS Plus volume.
** Checking Extents Overflow file.
   Invalid index link
(3, 230)
** Repairing volume.
** Rechecking volume.
** Checking HFS Plus volume.
** Checking Extents Overflow file.
   Invalid index link
(3, 230)
** The volume Files could not be repaired after 3 attempts.
user@plug:~$ sudo fsck.hfsplus /dev/sda2
** /dev/sda2
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
   Invalid index link
(4, 396)
** Rebuilding Catalog B-tree.
** The volume   could not be repaired.

```

It seems to be the problem that the drives weren't unmounted cleanly so I was wondering if there's a way to deal with this problem. I can't afford to re-format the drives (and certainly can't do it for another two months or so because I'm not in the country and am working via SSH).

Two questions arise:
a) How can I fix my drive
b) How can I (if I can) prevent this from happening in the future.

Oh, and I'm running Debian Squeeze compiled specifically for Kirkwood.

---

### Post by blueyelabs on 2010-02-12
I've tried mounting it and looking at the files and there seems to be no problem with that. The disk is not journaled so I don't know why I can mount it as read-only but not as read/write. I read somewhere about the use of a force option when mounting and I wonder if this would help?

Anyone?

---

### Post by blueyelabs on 2010-02-12
I tried using the force option but it still mounts as read-only.

To combat the question "Why are you using HFSPlus", the reason is because the file server acts as my TimeMachine backup for my mac so using hfs+ is the best option.

---

### Post by blueyelabs on 2010-02-16
Since no-one seems to have a solution to this, is there no way to use journaled HFS+ disks on linux? The journaling should solve this problem.

---

### Post by mw999 on 2010-03-01
Not a solution, just a comment.

This happens every time I mount my non-journalled HFSplus file system read-write. On the same system as yours. I don't need an "unclean" shutdown to generate the error.

Something adrift, somewhere.

---

### Post by blueyelabs on 2010-03-02
The HFS+ support in linux is beyond dodgy. It's a pile of rubbish.
I cannot remember how I got my HFS+ disks to mount as rw but there's a guide on here somewhere I think. Since I have not actually followed it I can't tell you if it's the same method I used but it probably works.

This is frustrating.

---

