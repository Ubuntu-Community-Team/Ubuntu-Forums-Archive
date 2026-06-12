---
title: "MD5SUM to produce not ok files"
date: 2009-07-10
forum: General Help
---

### Post by popeye on 2009-07-10
Hello,

I have copied my files on a external harddisk and created a md5sum file from the original with this command

```
find . -type f -print0 | xargs -0 md5sum > /home/erik/MD5SUMsda1.txt 

```

When i check all the files on the external harddisk 2 files are not ok, but i don't know how to find those files. md5sum only produces a message 2 files are not ok.

The man page of md5sum doesn't help me further.

---

### Post by popeye on 2009-07-11
After a bit more search on google i found the solution to my needs on [HTML]http://www.linuxquestions.org/questions/showthread.php?p=3369336#post3369336[/HTML]

```
md5sum -c file.md5 | grep FAILED$ > failed_hashes
md5sum -c file.md5 | grep -v OK$ > failed_hashes
```

It might be useful for someone else.;)

---

