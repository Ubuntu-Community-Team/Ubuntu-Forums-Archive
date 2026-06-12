---
title: "Can't see files on mounted partitions"
date: 2011-05-14
forum: General Help
---

### Post by sennett on 2011-05-14
I'm trying to recover data off an old internal laptop drive inside a USB caddy.  It has three partitions, one of which does not mount automatically, but I can mount it and see the files in the terminal.  The other two mount automatically on ```
/media/ACER
``` and ```
/media/5E93-A93D
``` when I plug the hardrive in, but I can't see any files on them - they appear empty in Nautilus/Thunar and the terminal.  I know there are two FAT32 filesystems there, one with Windows XP on, and another that I used for My Documents.  As far as I remember they were both nearly full.

They show up on system monitor as being empty.  When I run GParted I get these confusing results:

[IMG]http://i55.tinypic.com/2w6tbus.png[/IMG]

this was after I mounted 'PQSERVICE' partition on '/media/sdc1', which mounts without any issues (albeit not automatically).

I have tried using [ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html") to get the files off, but I could only get it to output a single file (I was after a directory structure), and the file that it did output was completely empty, so I guess ddrescue can't see anything there either.

Does anyone know what is going on?

---

### Post by jerrrys on 2011-05-16
your fat files are showing empty.  you are sure 'sdc' is the right drive ?

---

