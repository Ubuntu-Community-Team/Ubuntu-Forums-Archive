---
title: "Removing files from multiple directories using rm"
date: 2011-07-14
forum: General Help
---

### Post by luotinen on 2011-07-14
Hi!

I have a lot of files that are inside directories like this:

/abc/abc1234.JPG
/def/abc5678.JPG
/dsadas/abc9012.JPG
...

The files have a common start and end (abc*.JPG) but they are contained in multiple directories with various names and the amount of the files varies. How can I remove them with the rm command?

I tried 

rm abc*.JPG -R

in the parent directory, but it does nothing.

---

### Post by bodhi.zazen on 2011-07-14
Take a look at find ;)

[http://content.hccfl.edu/pollock/unix/findcmd.htm](http://content.hccfl.edu/pollock/unix/findcmd.htm)

```
find . -name abc\*.JPG
```

should get you started ;)

---

### Post by nothingspecial on 2011-07-14
If the directories are only one deep (so to speak), then ```
rm */abc*.JPG
``` will do it, without the need for find.

---

