---
title: "Question about writing to ntfs with new kernel"
date: 2006-04-20
forum: General Help
---

### Post by cooldudejz on 2006-04-20
can the newest release of dapper read and write to the ntfs filesystem. i was recently given a new computer with a XP hard drive packed full of trojans, but i can not fix it right now. according to wiki all kernels 2.6.14 and up include FUSE. so can i write to an ntfs drive with the beta release of dapper. thanx

---

### Post by ronmarley1 on 2006-04-20
I'd like to know the answer to this too.

---

### Post by Computeruser on 2006-04-20
Have you considered using a BartPE boot CD, booting the XP system with Bart and then dealing with the system that way? BartPE is a bootable XP CD and works just fine with NTFS disks.

---

### Post by az on 2006-04-20
[https://wiki.ubuntu.com/Lkraider/NtfsFuse?highlight=%28fuse%29](https://wiki.ubuntu.com/Lkraider/NtfsFuse?highlight=%28fuse%29)

The question is how good is fuse?

---

### Post by az on 2006-04-20
I edited the page to mention installing the libfuse2 and ntfsprogs packages in Dapper.


I wrote a file to an ntfs partition and booted into windows (the only reason I have to boot into windows) and it was there.  I don't use windows so I don't know if the partition is dammaged, really, but it seems fine.

---

