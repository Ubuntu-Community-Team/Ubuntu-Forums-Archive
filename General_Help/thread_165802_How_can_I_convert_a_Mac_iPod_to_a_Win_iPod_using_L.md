---
title: "How can I convert a Mac iPod to a Win iPod using Linux?"
date: 2006-04-25
forum: General Help
---

### Post by Entity on 2006-04-25
Hi,

I have a HFS+ formatted iPod (a Mac iPod) I would like to convert to FAT32 iPod (Win iPod). But since I dont't Windows installed anywhere I would to proceed under linux (Ubuntu Dapper Drake).

Any idea?

---

### Post by jazzmuzik on 2006-04-25
I haven't tried this, so it's a guess. Look at /sbin/mkfs.vfat to format the drive with FAT32. If necessary, use fdisk to delete and create partitions.

---

### Post by Entity on 2006-04-25
[QUOTE=jazzmuzik]I haven't tried this, so it's a guess. Look at /sbin/mkfs.vfat to format the drive with FAT32. If necessary, use fdisk to delete and create partitions.[/QUOTE]
Well I think the iPod has a firmware I must preserve. I doubt it's simple as you explained.

---

### Post by jazzmuzik on 2006-04-25
Probably not. I was just throwing a suggestion at you. But formatting a drive won't affect its firmware. Firware, by definition, is "firm" because it exists in a read/write chip, not on the hard disk.

But maybe you meant the firmware needs to be updated in addition to the formatting? That may be true if they use a different firmware for the Win32 vs. HFS+ versions of the ipod. I was assuming they would use a common firmware.

---

### Post by Pcmikepl on 2006-05-03
Accually the iPod has two partitions, a small one at the beginning for the firmware (not a ext3/fat or HFS) and followed by the "main" partition where the iTunes Database and your music is stored.

---

### Post by aysiu on 2006-05-03
Can't the firmware just be reinstalled after you format the iPod?

---

### Post by Pcmikepl on 2006-05-04
It can be restored BUT I dont know if the firmware for the Mac iPod or the Windows one are the same, if they are this is possible. But it is much easier to just go over to a friends house and run the firmware upgrade than to do it in linux.

There would be no problem if Apple just ported the iPod and iTunes software to linux.......

---

