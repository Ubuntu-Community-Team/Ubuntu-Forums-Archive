---
title: "Ubuntu is not auto-mounting CDROM, USB Flash/External drives or NTFS XP partition"
date: 2011-01-18
forum: General Help
---

### Post by diablo75 on 2011-01-18
For quite a while now I've noticed that Ubuntu stopped listing my Windows XP partition in my Places menu like it used to but let it go because it wasn't something I needed to access often.  But now I'm discovering that Ubuntu is also not mounting my DVD drive when I put a CD in, nor my USB flash drive that I just reformatted to NTFS using gparted within Ubuntu, nor does any other external USB drive.  I don't know how to start with troubleshooting the cause.  Any ideas?

---

### Post by diablo75 on 2011-01-20
Bump.

---

### Post by diablo75 on 2011-01-23
Bump?

---

### Post by Mikhail Titov on 2011-07-29
Can you launch disk manager "palimpsest"? If during repartitioning you happened to have so called empty partition as reported by fdisk
```
mlt@nb:~$ fdisk -l
omitting empty partition (5)
...
```you have a chance that udisks daemon doesn't recognize some extended partitions and it may cause problems with libgdu and a bunch of other things including automounting, update-notifier crash, disk manager crash, and so on.
If this is the case check this [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/571038](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/571038) for a possible patch.

---

