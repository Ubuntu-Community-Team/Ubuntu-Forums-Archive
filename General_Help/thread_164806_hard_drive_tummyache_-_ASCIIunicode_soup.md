---
title: "hard drive tummyache - ASCII/unicode soup?"
date: 2006-04-23
forum: General Help
---

### Post by brallan on 2006-04-23
EDIT: I figured out how to remove all of the encoding errors from the drive, by using a tool called Thunar Bulk Renamer, when there are invalid encodings throughout an entire drive. These are the typical "invalid encodings" that happen when passing a filesystem from NTFS to fat32 to ext3, etc, and prevent files from being comfortably moved/copied thereafter.

    All you have to do is search for * in nautilus (to find all of the files on the drive) organize by filetype, select all but the directories, and drag them into the window of the bulk renamer. It works great. You have to do directories manually, since subdirectories or files will not be found by the bulk renamer once the directory name has changed, and will give an error message.

Quodlibet also has a similar bulk renaming function which removes non-ascii letters, but can also do a similar thing, probably only for music files, and does not have an option to leave the original name as is....
++++++++++++++++++++++++++++++++++++++
ORIGINAL POST:
I have a lot of music and data in spanish, turkish, russian, etc. Unfortunately, this (ext2) drive is full of thousands of filename errors for any filenames that have non-english chars, and when I try to copy/open/use the files I get all kinds of error messages. The data inside the files seems fine.

BACKGROUND: I bought a 200G external USB drive which came formatted with NTFS and soon had most of my data backed up on it. When I moved to ubuntu, I[ was frustrated]("http://www.ubuntuforums.org/showthread.php?t=151902") with ubuntu's inability to write to the drive so I [unfortunately decided]("http://www.ubuntuforums.org/showthread.php?t=151902") to change the drive to an Ext2 partition. However, it was more data than could fit in one place, and in the process of moving the data off onto three other drives (FAT32, NTFS, ext3) and back onto the original drive, many of the filenames seem to have gotten corrupted, as they have non-english characters. This is probably because FAT32 does not support Unicode. 

Is there any command/utility to recover corrupted filenames? I don't care if the original characters are right, I just want to be able to use the files without error messages.

```
sudo e2fsck
``` returned:
```
/dev/sda1
e2fsck 1.38 (30-Jun-2005)
mp3s: clean, 14333/30539776 files, 18367505/61049000 blocks
```

> fdisk -l returned:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux
```

---

### Post by adamkane on 2006-04-23
Your message doesn't describe your problem in detail. Your post essentially says, "My filenames are all messed. Please help." If your filenames have mixed encodings, then you're only option may be to go through each file/folder one-by-one, and convert the filenames.

I've put together some methods to convert from one filename encoding to another. 

Howto:
[http://ubuntuforums.org/showthread.php?t=144297](http://ubuntuforums.org/showthread.php?t=144297)

Background:
[http://ubuntuforums.org/showthread.php?t=139154](http://ubuntuforums.org/showthread.php?t=139154)

Shell script to convert from NTFS -> UTF-8:
```

sudo apt-get install convmv
convmv -f cp850 -t utf-8 -r --notest *.* 

```

Nautilus script to convert from NTFS -> UTF-8:
```

#!/bin/bash
#NTFS to UTF-8

if [ $# -gt 0 ];then

    convmv -f cp850 -t utf-8 -r --notest "$@"| zenity --progress --pulsate --text="conversion in progress" --auto-close

fi
exit 0

```

Nautilus-script mini-Howto:
[http://g-scripts.sourceforge.net](http://g-scripts.sourceforge.net)

---

