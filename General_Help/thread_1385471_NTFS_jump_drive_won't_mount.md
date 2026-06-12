---
title: "NTFS jump drive won't mount"
date: 2010-01-19
forum: General Help
---

### Post by jimmy.eric on 2010-01-19
Well, I decided to upgrade all my computers from Windows 7 to Ubuntu 9.10.  However since on my laptop I didn't have too much data I threw it all on a 16GB jump drive which was formatted under windows 7 as NTFS.  However when I attempt to mount the drive I receive this error "The device  '/dev/sdb': doesn't seem to have a valid NTFS."  

Any idea how I might be able to get my data back?  I don't have a Windows operating system at my house so I'd prefer a solution using Linux.

---

### Post by fsando on 2010-01-23
> **jimmy.eric said:**
> Well, I decided to upgrade all my computers from Windows 7 to Ubuntu 9.10.  However since on my laptop I didn't have too much data I threw it all on a 16GB jump drive which was formatted under windows 7 as NTFS.  However when I attempt to mount the drive I receive this error "The device  '/dev/sdb': doesn't seem to have a valid NTFS."  

Any idea how I might be able to get my data back?  I don't have a Windows operating system at my house so I'd prefer a solution using Linux.

Did you install ntfs drivers in ubuntu?

Do a search in synaptics for 'ntfs'. You want ntfs-3g and likely ntfsprogs.

If this doesn't help you should check your drive with a windows machine.

---

