---
title: "tar.gz extract failure"
date: 2009-08-05
forum: General Help
---

### Post by sidewalkcynic on 2009-08-05
I seem to have lost the contents of tar.gz. When going through the extract process I get an error message, and seemingly nothing I can do - is there any way to recover anything? :confused:

---

### Post by oldos2er on 2009-08-05
Please post the error message.

---

### Post by sidewalkcynic on 2009-08-05
hey, now that sounds promising...

```
tar: Skipping to next header

gzip: stdin: invalid compressed data--format violated
tar: Child returned status 1
tar: Error exit delayed from previous errors

```

And then the big one:

> tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Skipping to next header
tar: Error exit delayed from previous errors


---

### Post by oldos2er on 2009-08-05
Sorry, I don't know what to suggest. Hopefully someone else will!

---

### Post by ibuclaw on 2009-08-05
Run
```
file **name_of_tarball**.tar.gz
```
and post the output.

where did you download the file from?


Regards
Iain

---

### Post by michy99 on 2009-08-05
Sounds like a corrupted file. If possible, try to download the file again.

---

### Post by sidewalkcynic on 2009-08-06
I created the archive myself as apart of the process for re-installing the OS with a better partitioning (experiement). I have seven partitions of documents plus the home folder and some other misc., so as it turned out two (300 Mb) of the nine (1.5 Gb) tar.gz failed. They wont be impossible to replace by revisiting the websites that can be recalled, but it will take time.

---

### Post by michy99 on 2009-08-06
Don't know if this will work, but it might be worth a try. First download this file:

[http://www.gzip.org/fixgz.c](http://www.gzip.org/fixgz.c)

Compile it with:```
cc -o fixgz fixgz.c
```To fix bad.tar.gz:```
./fixgz  bad.tar.gz  fixed.tar.gz
```

---

