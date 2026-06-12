---
title: "inconsistent file count"
date: 2012-10-01
forum: General Help
---

### Post by raydar on 2012-10-01
I've made several attempts to copy a folder containing around a hundred subfolders and many thousands of files from an external (USB) NTFS hard drive to my internal (SATA) ext4 hard drive. After the copy, the source and destination folders appear to have different numbers of files, on the order of several tens of files.

I get the same result copying both (1) via ethernet, with the source drive hooked to my NAS-capable router's USB port and shared with the destination computer by Samba, and (2) with the source drive plugged directly into the destination computer's USB port. 

Further, I've tried the copy operation using Nautilus and using Thunar; afterward, both file managers report different numbers of files in the source and destination folders, but the file managers do not agree on how many files or how much space they consume:

[INDENT]NAUTILUS (hidden files shown)
source 74,129 items, totalling 67.3 GB
destination 74,154 items, totalling 67.3 GB[/INDENT]

[INDENT]THUNAR (hidden files shown)
source 74,299 items, totalling 87.9 GB
destination 74,329 items, totalling 87.9 GB[/INDENT]

None of the files are in use during the copy. Some are hidden files, with names either starting with a . or ending with a ~, and by searching for ~ in Nautilus I did discover some discrepancies in the files copied whose names ended in ~ (these being GEdit backup copies, see [http://tombuntu.com/index.php/2008/01/10/dont-let-gnomes-text-editor-leave-hidden-files/](http://tombuntu.com/index.php/2008/01/10/dont-let-gnomes-text-editor-leave-hidden-files/) ). 

What's going on here? I want to make sure I have an exact duplicate of the directories and files I copy, like I seem to get with day-to-day copies of far more modest size. It makes me wonder how many times I've copied directories and not gotten a true duplicate without knowing it because I didn't compare file counts afterward. I'd have thought it might be an NTFS-versus-ext4 reporting difference of some kind, but given that Nautilus and Thunar don't even agree on the same drive (whether NTFS or ext4), I wondered if the copy was indeed exact but one or both file managers weren't counting files properly.

---

### Post by The Cog on 2012-10-01
I don't trust them GUI things for large numbers of files - try the command line, either cp or rsync.
```
cp -r src-dir dst-dir
```
or
```
rsync -a src-dir/ dst-dir
```

---

### Post by Stonecold1995 on 2012-10-01
You can tell the size of a directory in bytes with this (this command may take a while to complete with large directories):
```
du -sb /path/to/directory
```

---

