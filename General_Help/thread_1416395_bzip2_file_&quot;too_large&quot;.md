---
title: "bzip2 file &quot;too large&quot;"
date: 2010-02-26
forum: General Help
---

### Post by danielstrong52 on 2010-02-26
Hello there, I have been having a recurring problem backing up my filesystem with tar, using bzip2 compression. Once the file reached a size of 4Gb, an error message appeared saying that the file was too large (I closed the terminal so do not have the exact message. Is there a way to retrieve it?). I was under the impression that bzip2 can support pretty much any size of file. It's rather strange: I have backed up files of about 4.5Gb before without trouble. At the same time, I have had this problem before, and it's definitely not a memory problem: I am backing up onto a 100G external hard drive.

That reminds me, in fact, (I hadn't thought of this) that one time I tried to move an archived backup of about 4.5Gb to an external (it may have been the same one) and it said that the file was too large. Could it be that there is a maximum size of file I can transfer to the external in one go?

Before I forget, I have ubuntu Karmic and my bzip2 version is 1.0.5 (and tar 1.22, though maybe this is superfluous information?)

Thanks for your help.

Dan

---

### Post by iponeverything on 2010-02-26
what type of filesystem are you creating the file on?

---

### Post by rnerwein on 2010-02-26
hi
i guess is a problem of the filesystem type - have a look at:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)
there is a description of all ( nearly ) filesystem types

ciao

---

### Post by steviefordi on 2010-02-26
Sounds like you're creating the file on a FAT32 filesystem which I believe has a 4Gb limit.

---

### Post by danielstrong52 on 2010-02-27
Yep, that's the problem. Thanks for the help!

---

