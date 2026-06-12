---
title: "Bulk file renaming"
date: 2010-11-11
forum: General Help
---

### Post by mtolsen on 2010-11-11
I have >100000 files (in >1000 folders) that I want to rename. The file names are of the format AAAA_BBBB_CCCCCCCCCCCD_EE.ext. The AAAA part needs to be removed (which is fairly simple) and the BBBB and D forms a unique ID that should be kept. The tricky part is the CCCCCCCCCCC and EE which combine to form a unique ID that I want to change to another ID according to a (long) list of ID1=ID2 rules. 
 
Does anyone know of a script/software that can perform this renaming based on a list of rules??
 
Thanks!!

---

### Post by HermanAB on 2010-11-11
Hmm, you can do that with a combination of find, sed and awk.  A weekend worth of Googling and experimenting should get you going...

---

### Post by sohlinux on 2010-11-11
I use krename gui

---

### Post by Cheesehead on 2010-11-11
You have a couple issues here.

First, you need to keep the logic of each filename change transparent, because SOMETHING will come out wrong, and you'll need to debug it. Sed and awk are vastly cool, but hard to read and debug clearly. Python or another more verbose language make more sense for it, and are much easier to add debugging statements and tools. The entire program is much longer, but it's easier for you to read, understand, and fix.

A Python example:
```
old-filename = get-file-name(folder)
BB = old-filename.split('_')[1]
CC = old-filename.split('_')[2][0:-1]
DD = old-filename.split('_')[2][-1:]
EE = old-filename.split('_')[3][0:-4]
BD = make-id(BB, DD)
CE = convert-id-based-on-rules(CC, EE)
new-filename = make-new-filename(BD, CE)
rename(old-filename, new-filename)
log(old-filename, new-filename)
```

Second, with so many files, you're going to want something that digs through each folder automatically, and logs its changes. So you can check the status, find out what it actually did, and track down files affected by any errors. Again, a more verbose language is your friend here.

I'll ignore the third issue, which is 'shouldn't something like this be in a database?' because it's not relevant.

---

