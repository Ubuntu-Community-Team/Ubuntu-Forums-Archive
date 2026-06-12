---
title: "Use fast drive as fileserver cache?"
date: 2010-09-24
forum: General Help
---

### Post by zymurgist on 2010-09-24
I have ubuntu lucid lynx server running on an old eMachine as a fileserver. It has a big (2TB) slow (10-20 MB/s) external drive (ntfs-3g), and a small (20G) fast (60 MB/s) internal drive (ext3).

Using smbfs and vsftpd and sshd, all my data lives on the big drive and I'll see dramatic speed differences between the drives.

I'm wondering, is there a way to things up so that the external drive uses a cache on the internal drive to speed things up? 

For example ... ftpd takes data from a client, and instead of slowly writing it directly to the external drive, it is written first (and quickly) to the internal drive, then, later, it is written to the external drive?

---

### Post by dcstar on 2010-09-25
> **zymurgist said:**
> I have ubuntu lucid lynx server running on an old eMachine as a fileserver. It has a big (2TB) slow (10-20 MB/s) external drive (ntfs-3g), and a small (20G) fast (60 MB/s) internal drive (ext3).
.......

Why are you using such an old filesystem on the external drive?

Reformat it to something more modern and efficient.

---

### Post by zymurgist on 2010-09-25
The last time I did that and needed to attach it to a windows box I was screwed.

Besides, I doubt that will speed things up.

---

