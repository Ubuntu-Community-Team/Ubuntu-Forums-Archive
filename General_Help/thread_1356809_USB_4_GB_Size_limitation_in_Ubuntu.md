---
title: "USB 4 GB Size limitation in Ubuntu"
date: 2009-12-16
forum: General Help
---

### Post by simartem on 2009-12-16
I have got a 16 GB Toshiba USB stick. It seems to be in FAT32 file system, when i try to copy files larger than 4 GB it is giving me errors. Which filesystem should I format the USB to get ability for copying bigger files than 4 GB ? Ubuntu 9.10

---

### Post by prem1er on 2009-12-16
If you are using it strictly with *nix system you are safe to put a ext3 file system on it. If you know that you will need to copy files to/from windows at some point ntfs would be a better bet.

---

### Post by Sef on 2009-12-16
If you are going to be using it strictly with GNU/Linux, then you can format it as ext3 or ext4.  If you are going to be using it with Windows, then use NTFS.

---

### Post by prem1er on 2009-12-16
Eerily similar.

---

### Post by simartem on 2009-12-16
I will use the USB Stick in GNU/Linux platform.. What i wonder is, is there any possibility to format the USB in NTFS format under Ubuntu ? My Gparted doesnt show the NTFS format option

---

### Post by ean5533 on 2009-12-16
> **simartem said:**
> I will use the USB Stick in GNU/Linux platform.. What i wonder is, is there any possibility to format the USB in NTFS format under Ubuntu ? My Gparted doesnt show the NTFS format option

You need to install NTFS support (not installed by default). Run this:

```
sudo apt-get install gparted ntfs-3g ntfs-config ntfsprogs
```

gparted should be able to handle NTFS after that.

---

### Post by simartem on 2009-12-16
thanks ean5533, your explanation resolved my concern about the NTFS issue. Great tip.

---

### Post by iNaitvad on 2009-12-16
Fat32 only supports 2gb per file, its not an ubuntu problem. Btw if u format as NTFS you cant remove the memory, u should use safely remove (Fat32 doesnt have this issue). Hope this helps...

---

### Post by prem1er on 2009-12-16
> **iNaitvad said:**
> Fat32 only supports 2gb per file, its not an ubuntu problem. Btw if u format as NTFS you cant remove the memory, u should use safely remove (Fat32 doesnt have this issue). Hope this helps...

Fat32 supports up to 4GB, which the OP already knew.

---

