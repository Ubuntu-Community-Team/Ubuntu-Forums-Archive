---
title: "Error removing file: Directory not empty"
date: 2010-06-19
forum: General Help
---

### Post by dirgle on 2010-06-19
I'm having an issue deleting a few directories created by Sane Image Scanner.

First some details:
Im using Ubuntu  10.04 LTS
And Xsane version 0.996
The data in question is on an NTFS drive.

The issue:
I have been using Xsane to scan and create multi-page PDF's. The program creates a directory to keep the individually scanned images so they can be stiched together when all of them are scanned. Once done, it gives you the option to delete the directory it created and all its contents. The program deletes all the contents but fails to delete the directory. 

So then I try a shift-del from Nautilus. It return this error "Error removing file: Directory not empty.

Ok, next step I take is to open up a terminal and try to delete to from there

```
$sudo rm -rf /media/NTFS_Drive/PDF/Scanned/Latest_Documents
rm: cannot remove directory `/media/NTFS_Drive/PDF/Scanned/Latest_Documents': Directory not empty

```
It seems strange so I cd in to the directory and have a look using ls -al

and it returns this
```
$ ls -al
total 95864
drwxrwxrwx 1 root root     4096 2010-06-19 10:49 .
drwxrwxrwx 1 root root     4096 2010-06-19 10:23 ..
-rwxrwxrwx 1 root root 24536751 2010-06-19 09:57 .fuse_hidden000007360000003e
-rwxrwxrwx 1 root root 24536753 2010-06-19 10:01 .fuse_hidden0000073a0000003f
-rwxrwxrwx 1 root root 24536751 2010-06-19 09:59 .fuse_hidden0000073c00000040
-rwxrwxrwx 1 root root 24536753 2010-06-19 10:02 .fuse_hidden0000073f00000041

```
Ok what are these .fuse_hidden~ files, and how do I get rid of them. I tried deleting them individually through sudo but no luck. Any help would be appreciated. Thanks.

---

### Post by flitbee on 2011-05-30
I've run into the same problem. I deleted some MP3 files via the Banshee music player. It left a file named ".fuse_hidden0000041b00000017" which I an unable to delete (either via Windows or Ubuntu including via termial). Any idea anyone?

When I do an ls on the directory I see some files that I had deleted earlier appear in a Turquise colour:

[COLOR=DarkSlateBlue]ls: cannot access Song.mp3: No such file or directory
-????????? ? ?       ?           ?                ? Song.mp3
[/COLOR]

---

