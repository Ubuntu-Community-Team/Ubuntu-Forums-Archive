---
title: "Copy files from multiple directors"
date: 2009-11-03
forum: General Help
---

### Post by kumoshk on 2009-11-03
I have a whole bunch of files, and each file is in its own folder. The problem is, I want them all in the same folder (instead of in unique ones). I'd rather not tediously copy and paste each file. How do I go about this?

At first I figured I could do something like this:
```
cp (or mv) -r *.ext someDirectory
```
But alas, it doesn't seem to work.

Any ideas?

Way back when I used Windows, I solved this problem by a GUI search for all files of that type in the folder, and then I cut them from the find window and pasted them to their new destination. The find program with Ubuntu doesn't seem to allow for copying/cutting/etc., however.

---

### Post by iMisspell on 2009-11-03
This might work for you...

Change the following to your needs...
main_search_dir=
save_dir=
extention=

```
#!/bin/bash

main_search_dir="/your/search/path/name/";
save_dir="/path/to/save/folder/";
extention="ext";

cp `find $main_search_dir -name "*.$extention"` $save_dir
```

It will search all the sub-directories and copy any file with specified extension to folder of your choice..


_

---

### Post by kumoshk on 2009-11-03
> **iMisspell said:**
> This might work for you...
Thanks. That mostly did the trick—all except one file, since it had a space in it (and find doesn't encapsulate what it returns in quotes, apparently—or something). So, if anyone knows a way to get multiple-word files to work (for future reference), please let me know. Thanks!

---

