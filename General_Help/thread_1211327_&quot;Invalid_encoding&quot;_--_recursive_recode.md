---
title: "&quot;Invalid encoding&quot; -- recursive recode?"
date: 2009-07-12
forum: General Help
---

### Post by topdownjimmy on 2009-07-12
I have a ton of files that I pulled from an NTFS drive, and many of them that contained foreign characters in the filename now have question mark characters in place of the foreign characters, and the label "(invalid encoding)" tacked to the end of them.

I saw in [this thread](http://ubuntuforums.org/showthread.php?p=325234) that there is something called "recode" that can help to convert the encoding to Linux's UTF-8.

My first question is whether there is a command to apply this recode to all files in a directory and its subdirectories recursively.

My second is how to determine the existing encoding on a file.

Thanks.

---

### Post by 80aless on 2009-10-31
maybe this? 
[http://ubuntuforums.org/showthread.php?t=1239904](http://ubuntuforums.org/showthread.php?t=1239904)

---

### Post by 80aless on 2009-12-20
Try this instead:
convmv -r --notest -f windows-1255 -t UTF-8 *

---

