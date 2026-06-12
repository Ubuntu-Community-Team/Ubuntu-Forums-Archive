---
title: "uuid only 8 digits?"
date: 2009-12-18
forum: General Help
---

### Post by garyed on 2009-12-18
I was checking my drives uuid & found two drives with 32 digits but my third drive only had 8 digits. Could it have anything to do with it being formated fat32?

---

### Post by bodhi.zazen on 2009-12-18
> **garyed said:**
> I was checking my drives uuid & found two drives with 32 digits but my third drive only had 8 digits. Could it have anything to do with it being formated fat32?

It has everything to do with FAT =) (although I do not know the technical details).

---

### Post by fragos on 2009-12-18
I did some experimenting and indeed VFAT formated SD cards have 8 digit UUID's. SD cards formated to ext2 has the same longer UUID's that you disk has. It would appear to be a FAT thing.

---

### Post by dcstar on 2009-12-19
> **fragos said:**
> I did some experimenting and indeed VFAT formated SD cards have 8 digit UUID's. SD cards formated to ext2 has the same longer UUID's that you disk has. It would appear to be a FAT thing.

FAT & NTFS partitions do not actually support UUID, the value displayed is generated (somehow) for compatibility purposes. FAT UUIDs always seem to be 8 characters, NTFS 16 characters.

The code seems to be in the /cvs/hal/hal/hald/linux/volume_id code tree for those that want to look it up....

---

