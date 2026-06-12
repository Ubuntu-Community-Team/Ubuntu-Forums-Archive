---
title: "Lost SD Card"
date: 2011-06-28
forum: General Help
---

### Post by maxwjackson on 2011-06-28
Alright so I lost a sd card that I had uploaded to my comp before it crashed but I wiped the card before I lost it and I want back what was on it..I have ran testdisk and photorec and it has only brought me back 5 or so pics, but when I search the card in deleted files through either program it lets me see the file names, and when I try to save it the computer doesnt read the jpeg file when I go to open the recovered file. 

Does anyone have any ideas? I would love to have this stuff back if possible!!

Thanks in advance!

---

### Post by An Sanct on 2011-06-28
Files are actually not *deleted* from FAT partitions, when you delete them. Only the reference to where they are (in the FAT table) is marked to be "not wisible", actually IF you would see the file names they would be
```
?icture.jpg
```
for a file, that preiously was
```
picture.jpg
```
followed by a range of sectors, which are *now* not treated as owned anymore (since the file was deleted...)

If you used the card at any point between when you deleted things from it and the point when you want to restore (undelete) files, then data went lost - overwritten by other applications and/or files, since the space, that formerly was reserved by the picture "picture.jpg" was now not marked as "owned by a file" in the FAT table, thus making it free for writing.

If you recover such files, mostly you will get garbage - parts of files, that are not the file you want and corrupt the image.

---

