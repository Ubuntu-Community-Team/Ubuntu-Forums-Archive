---
title: "Best way to compress and split a large file up?"
date: 2006-02-22
forum: General Help
---

### Post by donjjones on 2006-02-22
I'd like to compress a single 16GB file in one directory into several smaller 650m files into another directory.  Is there a way to do this with tar and split?  I've tried everything I could find in google searches and nothing seems to work at all.  Any suggestions?

Thanks!
DJ

---

### Post by JoshuaPDavis on 2006-02-22
cd /the/directory/i/want/my/files/to/go/to
tar -cvj /full/path/to/mybigfile | split -b 650m

---

### Post by donjjones on 2006-02-22
Thanks much for the reply!  I started it and it looks like it names the files xxa, xxb, and so on.  Any way to make it the way you want?  For example file-xxa, file-xxb, etc.  Or maybe event file.001, file.002....

---

### Post by Ramses de Norre on 2006-02-22
Just to know: how do you put it back together then?

---

### Post by nrwilk on 2006-02-22
[QUOTE=Ramses de Norre]Just to know: how do you put it back together then?[/QUOTE]
Word, I was going to ask too.

---

### Post by oakz on 2006-02-22
$ cat file1 file2 file3 > newfile

---

### Post by nrwilk on 2006-02-22
why is it always so incredibly simple that we wouldn't have thought of it?  :p :) :-D :mrgreen:

---

### Post by gunnar_steinn on 2006-02-22
or just $cat file* > largefile - since it seems like you are going to have  a lot of files! :)

---

### Post by krazykit on 2006-02-22
When you do this, it wouldn't be a bad idea to check the md5sums, just to make sure nothing screwed up.  Since it sounds like you're transferring with optical media... well, better safe than sorry.

---

### Post by donjjones on 2006-02-22
Any way to make the split files different than xxa, xxb, etc?

---

### Post by ow50 on 2006-02-22
[QUOTE=donjjones]Any way to make the split files different than xxa, xxb, etc?[/QUOTE]
```
SYNOPSIS
       split [OPTION] [INPUT [PREFIX]]

DESCRIPTION
       Output  fixed-size  pieces  of INPUT to PREFIXaa, PREFIXab, ...; default
       PREFIX is ‘x’.  With no INPUT, or when INPUT is -, read standard  input.
```
and maybe
```
       -d, --numeric-suffixes
              use numeric suffixes instead of alphabetic
```
=> split -b 650m -d BIGFILE "man_rules-"

---

### Post by donjjones on 2006-02-22
I must be doing something wrong here - here's my commands and output:

```

me@ubuntu:/media/usbdisk$ tar -cvj /home/me/bigfile.txt | split -b 650m -d "splitupfile-"
split: splitupfile-: No such file or directory
tar: Removing leading `/' from member names
/home/me/bigfile.txt
me@ubuntu:/media/usbdisk$

```

Any ideas?

---

### Post by ow50 on 2006-02-23
[QUOTE=donjjones]I must be doing something wrong here - here's my commands and output:[/QUOTE]
If the output is not piped to the end of the next command, you need to specify where the output is directed with a "-".
```
tar -cvj /home/me/bigfile.txt | split -b 650m -d - "splitupfile-"
```

---

### Post by pato101 on 2006-02-23
The split names are convenient to do
cat * > largefile
Note that altering the order would damage the recovered file! so xaa, ... are names to be in correct order.

---

### Post by donjjones on 2006-02-23
Thanks much!  That did the trick!

---

