---
title: "tar and gzip at same time from one command"
date: 2012-10-12
forum: General Help
---

### Post by wh33t on 2012-10-12
Hey forums,

I'm writing a back up script and I'd like to tar a directory called "/current/" and gzip it at the same time.

So far I have tried $ tar -cf <folderpath> > gzip -9 archive.tar.gz and it keeps telling me I'm cowardly trying to create a file with out a name.

Any help would be great :D

---

### Post by pqwoerituytrueiwoq on 2012-10-12
```
tar czvf myfolder.tar.gz abcfolder/
```
source:
[http://www.neohide.com/tar-gz-a-quick-and-easy-compression-and-extraction-command-line](http://www.neohide.com/tar-gz-a-quick-and-easy-compression-and-extraction-command-line)

---

### Post by wh33t on 2012-10-12
> **pqwoerituytrueiwoq said:**
> ```
tar czvf myfolder.tar.gz abcfolder/
```
source:
[http://www.neohide.com/tar-gz-a-quick-and-easy-compression-and-extraction-command-line](http://www.neohide.com/tar-gz-a-quick-and-easy-compression-and-extraction-command-line)

Oh wow, Tar has that built in? How would I set the compression to maximum with that command? I know gzip -9 will do this.

---

### Post by pqwoerituytrueiwoq on 2012-10-12
```
GZIP=-9 tar cvzf file.tar.gz /path/to/directory
```
assuming this is a bash script
source:
[http://superuser.com/questions/305128/how-to-specify-level-of-compression-when-using-tar-zcvf#answer-305141](http://superuser.com/questions/305128/how-to-specify-level-of-compression-when-using-tar-zcvf#answer-305141)

---

### Post by wh33t on 2012-10-12
> **pqwoerituytrueiwoq said:**
> ```
GZIP=-9 tar cvzf file.tar.gz /path/to/directory
```
assuming this is a bash script
source:
[http://superuser.com/questions/305128/how-to-specify-level-of-compression-when-using-tar-zcvf#answer-305141](http://superuser.com/questions/305128/how-to-specify-level-of-compression-when-using-tar-zcvf#answer-305141)

According to your source there seems to be some debate over whether or not that will work. 

Also I see in multiple places on the web that gzip is not the greatest anymore. Is there a way to invoke tar with 7zip or bzip2 or something else that's better? Speed is not really important as the compression could take up to 24 hours and I would be ok with that. I just need to cram as much data as possible into a 2Tb Raided array.

---

### Post by wojox on 2012-10-12
pipe it
```
tar cvf - /path/to/directory | gzip -9 - > file.tar.gz
```

---

### Post by kjohri on 2012-10-13
In order to use bzip2 for compression, try

```
tar -cvjf myfolder.tar.bz2 /path/to/directory
```

---

### Post by wh33t on 2012-10-13
> **kjohri said:**
> In order to use bzip2 for compression, try

```
tar -cvjf myfolder.tar.bz2 /path/to/directory
```

Thank you! That's actually what I ended up doing. 

I'm curious though, does it matter if I call it a tar.bz2 versus a tar.gz? I suppose it would make it confusing for an outsider to try and unpack the archive but the file extensions don't really make a difference do they?

I'd also like to know what extension people use for the LMZA compression. Would it be tar.lmz?

---

