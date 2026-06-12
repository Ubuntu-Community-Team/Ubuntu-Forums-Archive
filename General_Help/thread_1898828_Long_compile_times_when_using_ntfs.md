---
title: "Long compile times when using ntfs"
date: 2011-12-22
forum: General Help
---

### Post by trafo23 on 2011-12-22
Hi,
i have my code files on a ntfs partition which i mount in fstab as ntfs-3g. The problem is that it takes about 10 times longer to compile code when it is on a ntfs formatted partition. 

Clean build time when using ext4 is about 25 minutes but when i use ntfs its about 4 hours.

I ran hdparm tests on ext4 and ntfs partitions and they both say that the timing buffered disk reads speed is about 210 MB/sec.

What could be the problem?

Ubuntu 11.10 GDE & XP OS-s, a rather hip laptop with 4 cores and SSD drive in AHCI mode.

Thanks

---

### Post by davethewave83 on 2011-12-22
> **trafo23 said:**
> Hi,
i have my code files on a ntfs partition which i mount in fstab as ntfs-3g. The problem is that it takes about 10 times longer to compile code when it is on a ntfs formatted partition. 

Clean build time when using ext4 is about 25 minutes but when i use ntfs its about 4 hours.

I ran hdparm tests on ext4 and ntfs partitions and they both say that the timing buffered disk reads speed is about 210 MB/sec.

What could be the problem?

Ubuntu 11.10 GDE & XP OS-s, a rather hip laptop with 4 cores and SSD drive in AHCI mode.

Thanks
The developer of NTFS is Microsoft ;) 

why are you compiling off NTFS? Is there a reason you must? It could be the NTFS drive is fragmented and the ext4 isn't, so there is a seek-time influence to find free-space to write to, it could be because NTFS is not native to GNU/Linux. It could also be because of my first comment :P

---

### Post by Lars Noodén on 2011-12-22
I would also suggest moving off of NTFS, it is technically a very poor quality file system.  

Source code does not take much space, so if you really do have to use NTFS to share with Windows, then it would be better to do your work in EXT4 and just mirror the source code to the NTFS partition.  rsync is a good tool for that mirroring.

---

### Post by trafo23 on 2011-12-22
I keep files on ntfs because i want them to be accessible both in linux and windows, its quite a lot of gigabytes.

As i understand then ntfs-3g is a userspace level implementation.

I read that there should be some sort of kernel space support for that as well in newer kernels. How could i use that?

---

### Post by Lars Noodén on 2011-12-22
> **trafo23 said:**
> I keep files on ntfs because i want them to be accessible both in linux and windows, its quite a lot of gigabytes.

[rsync](https://help.ubuntu.com/community/rsync) would be good for syncing with minimal data transfer.  It copies only the changes so it would be easy to use to keep the two directories/partitions in sync.  

Otherwise you're going to be stuck with the limitations inherent in a shoddy file system like NTFS.

---

