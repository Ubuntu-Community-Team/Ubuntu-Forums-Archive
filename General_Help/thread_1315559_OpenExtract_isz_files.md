---
title: "Open/Extract isz files"
date: 2009-11-05
forum: General Help
---

### Post by chipfryer on 2009-11-05
I've not seen much on this in Ubuntu at all. Is there a program or method I can use to extract a isz archive please?

---

### Post by Giblet5 on 2009-11-05
.isz files are compressed .iso files.

```
gzip -d < mycdimage.isz > mycdimage.iso
```

should work, although I have never tried it.

Compressing an ISO image is kinda silly with disk space running $80/terabyte... My time is more valuable than that.

---

### Post by kanikilu on 2009-11-05
The OP of this thread doesn't say if it worked, but someone suggested using wine and a free windows utility to convert ISZ to ISO here: [http://ubuntuforums.org/showthread.php?t=1197625](http://ubuntuforums.org/showthread.php?t=1197625)

---

### Post by chipfryer on 2009-11-05
Thanks for the replies folks.

I get this from Terminal command line
"cannot execute binary file"

The program on the other thread will not load in wine 1.2. it just closes out.

I guess I'm stuck with finding a windows program that runs under wine now correct?
What a pain in the rectum. :mad:

Thanks again.

---

