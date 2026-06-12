---
title: "Advice request - Backing up the beast"
date: 2011-01-06
forum: General Help
---

### Post by bugsduggan on 2011-01-06
Firstly, if this is in the wrong category, I apologise.

I am looking for some advice on how best to backup my media (music/films etc) from one external USB drive onto another USB drive of the same make and model.

I know a simple cp command could do this but the drives are quite large and it would be nice to not have to copy everything every time I backup!

If anybody has any advice or suggestions, they would be most welcome.

---

### Post by seawolf167 on 2011-01-06
There are a number of ways to do this, my preferred method is to use [rsync]("http://ss64.com/bash/rsync.html")

If you want the same exact file structure & files with no compression you can do something like this:

```
rsync -r -v -u --delete /source/directory /destination/directory
```If, however, you want to compress the files, then you should use something like [tar]("http://ss64.com/bash/tar.html")

```
tar cvjf output-file-name.tar.bz2 /source/directory
mv output-file-name.tar.bz2 /destination/directory
```

---

