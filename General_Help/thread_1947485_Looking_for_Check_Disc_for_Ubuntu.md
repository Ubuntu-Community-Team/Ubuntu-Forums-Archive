---
title: "Looking for Check Disc for Ubuntu"
date: 2012-03-26
forum: General Help
---

### Post by oaxacamatt1 on 2012-03-26
Hi all,
I believe I have a rotten USB or at least some of it may be bad.  I would like to find an alternative to 'check disk' for Linux.  

Is there some way to check the integrity of my usb sector by sector.
Cheers

---

### Post by TeoBigusGeekus on 2012-03-26
If it's ntfs, I think it'd be better to find a windows pc.
If it's an ext filesystem, use fsck.

---

### Post by dcstar on 2012-03-28
> **oaxacamatt1 said:**
> Hi all,
I believe I have a rotten USB or at least some of it may be bad.  I would like to find an alternative to 'check disk' for Linux.  

Is there some way to check the integrity of my usb sector by sector.
Cheers

[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by Mark Phelps on 2012-03-28
USB sticks come preformatted with Windows filesystems on them.  Unfortunately, there is no "CHKDK in Linux that you can use to check those filesystems.  You need to plug them into an MS Windows PC and check them there.

---

