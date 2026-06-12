---
title: "Hard Drive Mistake - Missing Data"
date: 2010-05-02
forum: General Help
---

### Post by Thedjatclubrock on 2010-05-02
Misunderstanding software RAID and mdadm, I created an array of two identical ext4 filesystems raid-1, assuming it would work as I had intended. It didn't, and I am unable to mount the drives. I disassembled the array within 2 minutes. Is there any way to recover my filesystems? Thanks!:(

---

### Post by dino99 on 2010-05-02
as always before tweaking and taking risks, the clever way is to backup first, then is too late to whine.

cgsecurity.org tools may help

---

### Post by Thedjatclubrock on 2010-05-02
No joke - the drive with the backup failed. It just clicks, and doesn't even show up as an ATA device. Using fsck on an image I got some files, but not in any order.

---

