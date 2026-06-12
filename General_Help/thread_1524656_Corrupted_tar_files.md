---
title: "Corrupted tar files?"
date: 2010-07-05
forum: General Help
---

### Post by mr-pink on 2010-07-05
Hi all!

Some days ago I created some tar files to backup all my data and formatted my HD. The problem is that I cannot expand any of that files.This is what I get when I try expanding them:
```
$ tar -xvf thunderbird.bak.tar 
home/fabrizio/.thunderbird/
home/fabrizio/.thunderbird/appreg
home/fabrizio/.thunderbird/profiles.ini
home/fabrizio/.thunderbird/jj1ec4xx.default/
home/fabrizio/.thunderbird/jj1ec4xx.default/mimeTypes.rdf
home/fabrizio/.thunderbird/jj1ec4xx.default/panacea.dat
home/fabrizio/.thunderbird/jj1ec4xx.default/prefs-1.js
home/fabrizio/.thunderbird/jj1ec4xx.default/prefs-3.js
home/fabrizio/.thunderbird/jj1ec4xx.default/session.json
home/fabrizio/.thunderbird/jj1ec4xx.default/XUL.mfasl
home/fabrizio/.thunderbird/jj1ec4xx.default/folderTree.json
home/fabrizio/.thunderbird/jj1ec4xx.default/cert8.db
tar: Passaggio alla prossima intestazione
tar: Uscita con stato di fallimento in base agli errori precedenti

```I've seen there's a windows app called Advanced Tar Repair but it's not free (and it's only for win), so I'd prefer not using it, anyway I don't know if it would work.

I've also tried
```
 cpio -F backup2.tar.recovered -ivd 
```like suggested here [http://texasdrifter.blogspot.com/2007/10/failure-to-recover.html](http://texasdrifter.blogspot.com/2007/10/failure-to-recover.html) but it didn't work.

Don't know if it's important but I created that files on a HFS+ formatted HD

Please help me - I need that data

---

### Post by mr-pink on 2010-07-08
bump

---

### Post by AlphaLexman on 2010-07-08
what is the output of:
```
lsattr thunderbird.bak.tar
```

---

