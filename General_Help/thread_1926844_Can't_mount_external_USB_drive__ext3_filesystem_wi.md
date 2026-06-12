---
title: "Can't mount external USB drive / ext3 filesystem with UTF8"
date: 2012-02-17
forum: General Help
---

### Post by sambhogi on 2012-02-17
I have an old external drive that I want to copy data from. It is formatted as ext3 and it was used with Ubuntu previously, with no issues. Many of the file names use "special characters" and now in Oneiric these characters are not recognized and it's preventing me from copying the files. Manually mounting the drive with the utf8 option just prevents the mount from happening, returning the error:

[INDENT]EXT3-fs (sdb1): error: unrecognized mount option "utf8" or missing value[/INDENT]

Reading the man page, it appears that utf8 is not a supported option for ext3, yet the files were previously copied from an Ubuntu system to the drive with the very characters Oneiric is now barfing on.

If I mount without this option, everything is otherwise fine. This is very annoying. Any advice?

---

