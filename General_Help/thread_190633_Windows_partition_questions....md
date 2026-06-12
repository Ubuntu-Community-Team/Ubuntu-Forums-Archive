---
title: "Windows partition questions..."
date: 2006-06-06
forum: General Help
---

### Post by piracyrocks on 2006-06-06
Ok so i have my linux partitions and my windows partition.  I can access the files on my windows partition from linux but i cant write to it...is there any way i can be able to transfer files from my linux partition to my windows one?  all i really want to do is keep all my music on my windows partition and i cant do that if i download the music while in linux.

also, is there a way to make a shortcut to a directory?...i dont like having to go through each seperate folder click every time i wanna watch a movie.

---

### Post by yumigator on 2006-06-06
Instead of copying, you could just mount the NTFS partition with write access. A good tutorial can be found at [http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481). Alternatively, you can access an EXT2 filesystem in Winows by using the utility found at [http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html). I'm sure you could find EXT3 or ReiserFS utilities as well, but I haven't tried any of them.

As for your second question, you can right-click and create launcher. If you want symbolic links, however, you can use the ln command in Terminal.

---

### Post by givré on 2006-06-06
[QUOTE=piracyrocks]Ok so i have my linux partitions and my windows partition.  I can access the files on my windows partition from linux but i cant write to it...is there any way i can be able to transfer files from my linux partition to my windows one?[/QUOTE]
If your windows partition is in NTFS (as i guess) writing on it via linux is not really yet supported. You can, but it's still experimental, and some weird could happen. I suggest you to create an FAT32 partition where you will be able to share file between windows and linux

[QUOTE=piracyrocks]also, is there a way to make a shortcut to a directory?...i dont like having to go through each seperate folder click every time i wanna watch a movie.[/QUOTE]
Making a shortcut in linux is as easy as in windows, just right click on the file or the directery you want and select "Create a link"

---

### Post by piracyrocks on 2006-06-06
i want to make a shortcut to a directory, not a file, is there any way to do this?

---

### Post by givré on 2006-06-06
[QUOTE=piracyrocks]i want to make a shortcut to a directory, not a file, is there any way to do this?[/QUOTE]
That's the same

EDIT: i didn't translate very well the link location (i'm frensh), it should "make link"

---

### Post by mlind on 2006-06-06
Writing to NTFS share from linux isn't recommended, atleast it wasn't when I last
time tried it. You should probably read some experiences what other users have
had using fuse-ntfs or similar NTFS driver.

for creating symbolic links you can also use
```

ln -sf /path/to/link link_name

```

---

### Post by piracyrocks on 2006-06-06
thanks for the help guys

je parle francais.

---

