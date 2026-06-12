---
title: "Save files in JPG"
date: 2010-04-07
forum: General Help
---

### Post by Kangarooo on 2010-04-07
[http://lifehacker.com/software/encryption/hide-files-in-jpeg-images-207905.php](http://lifehacker.com/software/encryption/hide-files-in-jpeg-images-207905.php)
[http://www.online-tech-tips.com/computer-tips/hide-file-in-picture/](http://www.online-tech-tips.com/computer-tips/hide-file-in-picture/)
theres written how to save files in jpg file in windows
but how to do the same thing in ubuntu?

---

### Post by new_tolinux on 2010-04-07
As one of the comments in your second link state:
> @Juan
 This is actually just a concatenation of two files.
 Linux has a command cat to do just that:
 $> cat f1 f2 > f3
 I assume the reason this works is because the JPEG ends before the  RAR starts:
 The file contents are something along the lines of:
 JPEG header
JPEG data
JPEG end
+
RAR header
RAR data
RAR end
 The graphics program reads until the JPEG ends, and the RAR program  searches for the RAR header and reads from there. Whether or not the  de-compressor searches for the header (and doesn&#8217;t just start at the  beginning) determines whether or not the file can be read.
 I may be wrong though.
I haven't tried it ;)

---

