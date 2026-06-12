---
title: "External HD Input/Output Error"
date: 2009-10-15
forum: General Help
---

### Post by Featherbean on 2009-10-15
[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]I'm not sure this is even really an ubuntu issue, as my external hard drive worked fine with ubuntu for the past year and a half. Anyways, now I can't copy anything to it and every time I try to it gives me a the message "Error writing to file: Input/Output Error". I can copy files from the hard drive no problem. Also Nautilus doesn't seem to recognize the size of the disk.

I've also tried it on XP, but there I can't even see the files on the disk, it just prompts me to format the disk as soon as I try to open it.

I realize the simplest solution is probably just to reformat, but I was hoping I could fix it without doing this.

And if it helps:
```

sudo fsck /dev/sdb5
fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
Got 9125888 bytes instead of 30516048 at 16384
[IMG]file:///tmp/moz-screenshot-2.jpg[/IMG]
```

---

### Post by prshah on 2009-10-15
> **Featherbean said:**
> 
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action


I suggest you run testdisk (it's in the repos) on it, if you are going to take drastic measures on it in any case.

Testdisk can be used to check and restructure partitions and FAT tables if required.

---

### Post by az on 2009-10-15
> **Featherbean said:**
> 
I realize the simplest solution is probably just to reformat, but I was hoping I could fix it without doing this.


Well, if you can copy all your files, then it could be worse.

Don't try to fix the broken filesystem.  You can't rule out hardware problems and you shouldn't try to repair a filesystem on a bad drive.  That may result in actual data loss.

Backup and reformat.  Do a read/write test (several hours) when you reformat to see if there are any bad blocks.

---

