---
title: "Sort order question"
date: 2010-09-27
forum: General Help
---

### Post by richgriswold on 2010-09-27
I am used to the way that the old "C" locale sorts things.  For example, when I do a directory listing, I expect to see the dot files first, uppercase files next, and lowercase files last.  However, the C locale doesn't sort Unicode characters correctly, as this listing shows:

```
/tmp/test > LC_COLLATE=C ls -1a         
.
..
.File_a
File_a
file_a
file_e
file_f
file_é
```Another option is use to a locale such as en_US.utf8, which does sort Unicode characters correctly.  However, when I use this locale, files are sorted case insensitively, and the dot files are mixed with the regular files:

```
/tmp/test :) > LC_COLLATE=en_US.utf8 ls -1a
.
..
file_a
.File_a
File_a
file_e
file_é
file_f
```Is there any way that I can keep the "C" locale sorting behavior (dot files first, case-sensitive) but still get Unicode characters to sort correctly?

Thanks,
-Richard

---

