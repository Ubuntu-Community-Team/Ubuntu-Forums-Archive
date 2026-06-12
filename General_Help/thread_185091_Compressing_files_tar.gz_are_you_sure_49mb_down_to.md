---
title: "Compressing files tar.gz are you sure? 49mb down to 588kb"
date: 2006-05-31
forum: General Help
---

### Post by ade234uk on 2006-05-31
I just compressed a file in tar.gz format and it went from 49mb to 588kb are you sure? am I seeing things correctly?

I have dealt with tar.gz files before but never realised they compressed files so much. Amazing thing is It can now be emailed.

I wonder what it would come out as in a standard .zip?

---

### Post by Perfect Storm on 2006-05-31
I would check the compressed file first. It could have be messed up.

---

### Post by hw-tph on 2006-05-31
Pure text like source code can often be compressed a *lot*. Also try using bzip2 to create .tar.bz2 archives instead and marvel at the wonders of data compression: **tar cfvj filename.tar.bz2 <files>**.


Håkan

---

### Post by [LvN]N3misiS on 2006-05-31
Files with large amounts of redundancy can often be compressed by a large amount.

---

### Post by ade234uk on 2006-05-31
Its bloody amazing. Im well impressed with the compression. 

I will definately try 
bzip2 to create .tar.bz2 files and see what the compression is like on these files.

---

### Post by handy on 2006-05-31
So, did you decompress the file & check if it is still valid?

---

### Post by gumbald on 2006-05-31
It depends on what you're compressing entirely, stuff like mp3s will not go any further, they've already been compressed to within an inch of their life. Text documents have lots of free characters, which can be signified by a shorter string.

For some light reading...:

[http://en.wikipedia.org/wiki/File_compression](http://en.wikipedia.org/wiki/File_compression)

---

### Post by bruce89 on 2006-05-31
Just think what 7zip could do...

---

