---
title: "What filesystem is right for me?"
date: 2010-04-29
forum: General Help
---

### Post by Silver40mm on 2010-04-29
I have a hard drive that I want to be dedicated to music, and it needs to be able to be mounted by both Ubuntu and Windows 7. Which filesystem would be the best option?

Thanks in advance! =]

---

### Post by ubnoobie on 2010-04-29
> **Silver40mm said:**
> needs to be able to be mounted by both Ubuntu and Windows 7. Which filesystem would be the best option?


use a separate partition or hard drive for data to share between both ubuntu and win7, formatted with ntfs.

---

### Post by Don1500 on 2010-04-29
> **Silver40mm said:**
> I have a hard drive that I want to be dedicated to music, and it needs to be able to be mounted by both Ubuntu and Windows 7. Which filesystem would be the best option?

Thanks in advance! =]

A drive formatted to NTFS will be available to Ubuntu and any Windows.
A drive formatted to xfs, ext2, 3, or 4 will only be available to Ubuntu (or other Linux), and it will work better and never be fragmented. But windows can't see it.

---

### Post by SnickerSnack on 2010-04-29
I use vfat 32bit for my shared partition to ensure that any OS can read/write without any problems.  Ubuntu has ntfs reading built in and probably writing too.

---

