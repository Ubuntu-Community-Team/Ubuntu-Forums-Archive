---
title: "How to split large file"
date: 2012-06-04
forum: General Help
---

### Post by susja on 2012-06-04
Hello,
I wanted to copy big file ~ 5 Gb to my USB drive and realized that Ubuntu can't copy file larger than 4 Gb.
The only option is split and merge large file.
I was able to do it from command line using split command.
Are you aware of any friendly and reliable GUI based split/merge utility to do this?
Thanks,
P.S. I tried Gnome Split file splitter application in Ubuntu but it didn't work for me.
P.P.S. Well now I hit a real problem: I successfully split my 5 Gb file into 3 chunks using split command into USB drive  but when I tried to merge those chunks into 1 file I've got again error:
cat: write error: File too large

Any help?
Thanks

---

### Post by susja on 2012-06-04
Well I resolved my issue by reformatting USB flash drive from fat32 to ntfs.

---

### Post by idoitprone on 2012-06-05
> **susja said:**
> Hello,
I wanted to copy big file ~ 5 Gb to my USB drive and realized that Ubuntu can't copy file larger than 4 Gb.
The only option is split and merge large file.
I was able to do it from command line using split command.
Are you aware of any friendly and reliable GUI based split/merge utility to do this?
Thanks,
P.S. I tried Gnome Split file splitter application in Ubuntu but it didn't work for me.
P.P.S. Well now I hit a real problem: I successfully split my 5 Gb file into 3 chunks using split command into USB drive  but when I tried to merge those chunks into 1 file I've got again error:
cat: write error: File too large

Any help?
Thanks

that is not a ubuntu limitation, but a fat 32 limitation

If I you only sending to linux system or you own windows systems. I might consider ext2 

you can install a ext2 driver for windows
[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)
since it is stable and it is a linux file system. you get better read and write speeds

if you still have to talk to windows then ntfs is your best bet.
Never in your life format a file system to hts+ - that is a brain dead piece of crap

---

