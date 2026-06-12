---
title: "&quot;convert&quot; not working correctly?"
date: 2011-10-28
forum: General Help
---

### Post by Nixarter on 2011-10-28
I need to convert several jpeg's into a pdf file.  Convert does this apparently.  BUT, when I follow the exact guidelines, it won't work.  See my code...

```
ubuntu@ubuntu:~/Desktop$ convert *.jpg my_new.pdf
convert: unable to open image `*.jpg': &#65533;&#65533;> @ error/blob.c/OpenBlob/2489.
convert: unable to open image `*.jpg':  @ error/blob.c/OpenBlob/2489.
convert: missing an image filename `my_new.pdf' @ error/convert.c/ConvertImageCommand/2940.
```I checked several threads ([here]("http://ubuntuforums.org/showthread.php?t=808596") and other places) and they all say the same thing.  What am I doing wrong?

I even simplified all the names in the folder to 1.jpg, 2.jpg, and so on.  I tried just typing 1.jpg instead of using an asterisk (just to see if it would work for a single files, at least), but it didn't work.

---

### Post by Bobhuber on 2011-10-28
> **Nixarter said:**
> I need to convert several jpeg's into a pdf file.  Convert does this apparently.  BUT, when I follow the exact guidelines, it won't work.  See my code...

```
ubuntu@ubuntu:~/Desktop$ convert *.jpg my_new.pdf
convert: unable to open image `*.jpg': &#65533;&#65533;> @ error/blob.c/OpenBlob/2489.
convert: unable to open image `*.jpg':  @ error/blob.c/OpenBlob/2489.
convert: missing an image filename `my_new.pdf' @ error/convert.c/ConvertImageCommand/2940.
```I checked several threads ([here]("http://ubuntuforums.org/showthread.php?t=808596") and other places) and they all say the same thing.  What am I doing wrong?

I even simplified all the names in the folder to 1.jpg, 2.jpg, and so on.  I tried just typing 1.jpg instead of using an asterisk (just to see if it would work for a single files, at least), but it didn't work.
Didn't know imagemagick would do that with pdf but your right it should work. The program is telling you that it can't open the jpg files which sounds like the file permissions are wrong . Start by moving them into another directory /home/<username>/pictures and make sure you have read/write permissions on the files. Then make sure you open a terminal  NOT as ROOT before running the convert command.. Let me know how you make out.

---

