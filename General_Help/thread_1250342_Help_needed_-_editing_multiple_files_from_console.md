---
title: "Help needed - editing multiple files from console"
date: 2009-08-26
forum: General Help
---

### Post by zolero on 2009-08-26
**Hi everybody.**

I am adjusting a HTML documentation created by **doxygen**. The task is to move the **index** file to the toplevel directory, and **make all html files** in that folder to having their URL changed **to point to this index file**. But I need a shell command to do this at once on all 1774 files (to skip doing it manually, that is a real nightmare).

My pages' original code line:
```
<li><a href="index.html"><span>Main&nbsp;Page</span></a></li>
```

must be changed to:
```
<li><a href="../index.html"><span>Main&nbsp;Page</span></a></li>
```

Can anyone provide me with that command, please? Thanks in advance.

---

### Post by gldearman on 2009-08-26
You could try the procedure on [this page]("http://www.liamdelahunty.com/tips/linux_search_and_replace_multiple_files.php").  Except, obviously, replace "*.php" with "*.html"

```
perl -pi -w -e 's/<a href="index\.html">/<a href="\.\.\/index\.html">/g;' *.html
```

Or, if the files are in a whole bunch of subdirectories, do a find first, followed by an exec:

```
find . -iname "*.html" -exec perl -pi -w -e 's/<a href="index\.html">/<a href="\.\.\/index\.html">/g;' {} \;
```

But *check my syntax on either piece of code before you use it*.  I just threw it together as an example of how it could be done.  I'm not familiar enough with perl to guarantee that I did that right, and I didn't double-check the regular expressions.

And, y'know, back up those files first, of course.

---

### Post by zolero on 2009-08-26
Hi, **gldearman**.

You saved a lot of time for me. The first one worked like a charm. Saved this for future reference. Thanks a lot. \\:D/

Zolero.

---

