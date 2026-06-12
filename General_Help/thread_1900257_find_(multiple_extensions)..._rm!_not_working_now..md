---
title: "find (multiple extensions)... rm! not working now..."
date: 2011-12-25
forum: General Help
---

### Post by talz13 on 2011-12-25
I have an entry in my crontab to delete superfluous files from my unwatched videos directory.  Originally it was just used to remove "*.nfo" files, but now I have additional file extensions that I want to delete.  The new entry is ```
find /home/shares/video/unwatched/ -iname "*.jpg" -o -iname "*.tbn" -o -iname "*.nfo-orig" -exec rm -rf {} \;
``` I started out by surrounding the -iname parameters with parentheses like this \( ... \) but got errors, so I removed the parentheses.  I've run the find part of the command from the shell, and it returns everything I want to delete, but the -exec rm is not deleting the files.

I'm confused!

---

### Post by bodhi.zazen on 2011-12-25
You have to either use xargs or quote the {}

xargs

```
find <your optios> -print0 | xargs -0 /bin/rm -f
```

But that will fail if you have spaces in the file names.

quote the {}

```
find /home/shares/video/unwatched/ -iname "*.jpg" -o -iname "*.tbn" -o -iname "*.nfo-orig" -exec rm -rf '{}' \;
```

---

### Post by talz13 on 2011-12-26
> **bodhi.zazen said:**
> You have to either use xargs or quote the {}

xargs

```
find <your optios> -print0 | xargs -0 /bin/rm -f
```

But that will fail if you have spaces in the file names.

quote the {}

```
find /home/shares/video/unwatched/ -iname "*.jpg" -o -iname "*.tbn" -o -iname "*.nfo-orig" -exec rm -rf '{}' \;
```

I tried adding the single quotes around the {}, but it still wasn't deleting the files.  Strange!

---

### Post by bodhi.zazen on 2011-12-26
I see it is because you may only pass one set of results to a command, so write a script to loop through those one at a time.

---

### Post by sisco311 on 2011-12-26
Hmmm, your command will only delete the *.nfo-orig files. ;)

You probably want to delete the .jpg and .tbn files as well. Right?

```
find ./path \( -iname \*.jpg -o -iname \*.tbn -o -iname \*.nfo-orig \) -exec rm -i {} +
```

In this context, {} has no special meaning, so you don't have to quote it.

The **-exec command {} +** variant will run the command on a set of files instead of invoking the command for each file.

GNU find also has a -delete option.

**... -print0 | xargs -0 ...** should also do the trick and it should work with any filename.

For more info check out BashFAQ 075 (link in my signature).

---

