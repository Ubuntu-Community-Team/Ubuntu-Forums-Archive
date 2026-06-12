---
title: "memory stick copies folders but not files"
date: 2010-03-24
forum: General Help
---

### Post by editrix on 2010-03-24
This is too strange. I'm trying to copy my Kmail folders to a usb memory stick so I can import them on a new computer. Also my mp3 folder.

The folders and sub-folders copy onto the stick, but not the actual files. I've checked and there's plenty of room--the stick is empty.

```
/dev/sdb1           972M  8.0K  972M   1% /media/KINGSTON
```

I'm using Hardy. Any ideas?

EDIT: Google was no help on this. Maybe I phrased the questions badly. But the KDE site says:
> Problem: Cannot copy mail to a USB stick

Solution: Your usb stick is (V)FAT formatted, and thus can't handle maildir folder names (nor can it handle permissions, which can cause many other problems). You have two choices. Either format your usb stick as ext2 (in which case you should be aware it can't be read on windows OSes without installing additional software there) or create a tar file of all your mail, copy that to the stick and extract it to your new host.

I presume the way the MP3 files were named also caused problems. So I created tar files.

---

