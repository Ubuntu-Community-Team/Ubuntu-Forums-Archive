---
title: "Extract Multiple Files from command line"
date: 2009-09-04
forum: General Help
---

### Post by aqtivator on 2009-09-04
Hello.

I am a newbie when it comes to command line.

I have a directory of a personal wiki, which is full of files.

I tried to compress it from the command line. So I looked for tips and man pages, and being a little impatient did manage to compress it in to an .tar file, but all the inside files got compressed into .gz format individually...

So, now I have a wiki.tar file full of "file.php.gz" files :D 

what can I do to extract all the .gz files to their respective directories..

any help ( and criticism for not reading the docus well) is welcome

---

### Post by bodhi.zazen on 2009-09-04
tar xzvf wiki.tar

---

### Post by DaithiF on 2009-09-04
actually if i'm reading the original post correctly, he has an (uncompressed) tar file, whose contents are invdividually gzipped files.  In which case:
```
tar xvf wiki.tar
```   to extract the contents of the tar, and
```
find . -name '*.gz' -exec gunzip {} \;
```
to uncompress each file

---

### Post by aqtivator on 2009-09-08
> **DaithiF said:**
> actually if i'm reading the original post correctly, he has an (uncompressed) tar file, whose contents are invdividually gzipped files.
```
find . -name '*.gz' -exec gunzip {} \;
```
to uncompress each file

Ok solved, thank you guys for your help :)

---

